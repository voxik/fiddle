# Fiddle

[![Build Status](https://travis-ci.org/ruby/fiddle.svg?branch=master)](https://travis-ci.org/ruby/fiddle)

A libffi wrapper for Ruby.

Fiddle is an extension to translate a foreign function interface (FFI) with ruby.

It wraps [libffi](http://sourceware.org/libffi/), a popular C library which provides a portable interface that allows code written in one language to call code written in another language.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'fiddle'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install fiddle

## Usage

 Here we will use Fiddle::Function to wrap [floor(3) from libm](http://linux.die.net/man/3/floor)

```ruby
require 'fiddle'

libm = Fiddle.dlopen('/lib/libm.so.6')

floor = Fiddle::Function.new(
          libm['floor'],
          [Fiddle::TYPE_DOUBLE],
          Fiddle::TYPE_DOUBLE
        )

puts floor.call(3.14159) #=> 3.0
```

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake test` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/ruby/fiddle.


## License

The gem is available as open source under the terms of the [BSD-2-Clause](https://opensource.org/licenses/BSD-2-Clause).
