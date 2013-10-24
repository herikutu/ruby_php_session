# PHPSession
[![Build Status](https://travis-ci.org/Shinpeim/ruby_php_session.png?branch=master)](https://travis-ci.org/Shinpeim/ruby_php_session)

PHPSession is a php session file reader/writer. Multibyte string and exclusive control are supported.

When decoding php session data to ruby objects,

* Associative arrays in PHP is mapped to hashes in ruby.
* Objects in PHP is mapped to instances of Struct::ClassName in ruby.

When encoding ruby objects to php session data,

* Strings or symbols in ruby is mapped to strings in PHP.
* Instances of Struct::ClassName in ruby is mapped to a objects in PHP.
* Arrays in ruby is mapped to a associative arrays which's keys are integer in PHP.
* Hashes in ruby is mapped to a associative arrays which's keys are string in PHP.

## Installation

Add this line to your application's Gemfile:

    gem 'php_session'

And then execute:

    $ bundle install

Or install it yourself as:

    $ gem install php_session

## Usage
    # initialize
    session = PHPSession.new(session_file_dir, session_id)

    begin
      # load session data from file and obtain a lock
      data = session.load

      # save session and release the lock
      session.commit(data)

      # delete session file and release the lock
      session.destroy
    ensure
      # please ensure that the lock is released and the file is closed.
      session.ensure_file_closed
    end

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
