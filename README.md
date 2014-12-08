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
