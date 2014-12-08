Heroku buildpack: gdbm
=====================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) that
vendors gdbm.

It is meant to be used in conjunction with other buildpacks as part of a
[multi-buildpack](https://github.com/ddollar/heroku-buildpack-multi).

Structure and code shamelessly copied from [heroku-geo-buildpack](https://github.com/cyberdelia/heroku-geo-buildpack).

Usage
-----

Example usage:

    $ heroku config:add BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git

    $ cat .buildpacks
    https://github.com/StateAndPlain/heroku-gdbm-buildpack.git#v1
    https://github.com/heroku/heroku-buildpack-ruby.git#v129


Don't forget to pin buildpack versions you want to use in your .buildpacks file.

Testing
-------

```ruby 
>>> require 'gdbm'
=> true
```

Build Notes
-----------

The built-on-cedar-14 binaries that are downloaded by this buildpack, and live on s3, were created by the following, more or less:

* create a dummy cedar-14 heroku app and run bash on it with `heroku run bash`
* `wget gdbm.tgz ; tar -zxf gdbm.tgz ; cd gdbm`
* `./configure --prefix=/app/vendor/gdbm/1.11 ; make ; make install`
* `cd /app/vendor/gdbm/1.11 ; tar -czf ~/gdbm-1.11.tgz bin lib include`
