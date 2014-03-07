[![Gem
Version](https://badge.fury.io/rb/roomorama-validates_email.png)](http://badge.fury.io/rb/roomorama-validates_email)
[![Build
Status](https://secure.travis-ci.org/roomorama/validates_email.png?branch=master)](http://travis-ci.org/roomorama/validates_email)
[![Dependency
Status](https://gemnasium.com/roomorama/validates_email.png?travis)](https://gemnasium.com/roomorama/validates_email)

validates_email
===============

validates_email is a Rails gem that validates email addresses against RFC 2822 and RFC 3696

Installation
------------

  Add the following to your gemfile

    gem 'roomorama-validates_email', :require => 'validates_email'

Usage
-----

    class User < ActiveRecord::Base
      validates :primary_email, :email => true
    end

As well as any other Rails validation this one has the same triggers, such as `:on`, `:if`, `:unless`, `:allow_blank`, and `:allow_nil`.

Also, you can pass your own custom error message.

    class User < ActiveRecord::Base
      validates :primary_email, :email => { :message => 'is not an email address' }
    end

If you like to check MX Records for email, you can use `:mx` option.

    class User < ActiveRecord::Base
      validates :primary_email, :email => { :mx => true }
    end

And if you like to check MX Records with fallback to A record, use `:a_fallback` option.

    class User < ActiveRecord::Base
      validates :primary_email, :email => { :mx => { :a_fallback => true } }
    end

I18n
----

If you don't specify your own error message, then ActiveRecord's `:invalid` error message will be used to show the error.

If do check MX Records, then you have to specify your own error message or add it to your traslations:

    activerecord:
      errors:
        messages:
          mx_invalid: "is not valid"

Credits
-------

Based off the spectagor-validates_email gem.
Most of the code were taken from Alex Dunae (dunae.ca) plugin (see http://github.com/alexdunae/validates_email_format_of/) and adopted for Rails 3 playing around with Rails 3 beta, so pass all beers to him.

Contributors
------------

* Petr Blaho
* Christian Eichhorn
* Alexander Zubkov

How to contribute
-----------------

* Fork
* Make changes
* Write specs
* Do pull request

Testing
-------

To execute unit tests run `rake spec` within plugin folder.

The unit tests for this plugin use an in-memory sqlite3 database.

Notes
-----

Compatible with the following ruby versions:

* Ruby 1.8.7
* Ruby 1.9.3
* Ruby 2.0.0

Compatible with the following Rails versions:

* Rails 3.0.x
* Rails 3.1.x
* Rails 3.2.1
* Rails 4
