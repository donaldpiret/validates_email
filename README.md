= validates_email

validates_email is a Rails 3 plugin that validates email addresses against RFC 2822 and RFC 3696

== Installation

  rails plugin install git://github.com/spectator/validates_email.git

or

  gem 'spectator-validates_email', :require => 'validates_email'

== Usage

  class User < ActiveRecord::Base
    validates :primary_email, :email => true
  end

As well as any other Rails 3 validation this one has the same triggers, such as <tt>:on</tt>, <tt>:if</tt>, <tt>:unless</tt>, <tt>:allow_blank</tt>, and <tt>:allow_nil</tt>.

Also, you can pass your own custom error message.

  class User < ActiveRecord::Base
    validates :primary_email, :email => { :message => 'is not an email address' }
  end

If you like to check MX Records for email, you can use <tt>:mx</tt> option.

  class User < ActiveRecord::Base
    validates :primary_email, :email => { :mx => true }
  end

And if you like to check MX Records with fallback to A record, use <tt>:a_fallback</tt> option.

  class User < ActiveRecord::Base
    validates :primary_email, :email => { :mx => { :a_fallback => true } }
  end

== I18n

If you don't specify your own error message, then ActiveRecord's <tt>:invalid</tt> error message will be used to show the error.

If do check MX Records, then you have to specify your own error message or add it to your traslations:

  activerecord:
    errors:
      messages:
        mx_invalid: "is not valid"

== Credits

Most of the code were taken from Alex Dunae (dunae.ca) plugin (see http://github.com/alexdunae/validates_email_format_of/) and adopted for Rails 3, so pass all beers to him.

== Contributors

* Petr Blaho
* Christian Eichhorn
* Alexander Zubkov

== How to contribute

* Fork
* Make changes
* Write specs
* Do pull request

== Testing

To execute unit tests run <tt>rake spec</tt> within plugin folder.

The unit tests for this plugin use an in-memory sqlite3 database.

== Notes

Compatible with following ruby versions:
* Ruby 1.8.7
* Ruby 1.9.2
