# zodiac [![Build Status](https://travis-ci.org/7even/zodiac.svg?branch=master)](http://travis-ci.org/7even/zodiac) [![Gem Version](https://badge.fury.io/rb/zodiac.svg)](https://badge.fury.io/rb/zodiac) [![Gitter](https://badges.gitter.im/7even/zodiac.svg)](https://gitter.im/7even/zodiac)

This is a fork of http://github.com/7even/zodiac.

What's different:

- no active record methods
- different date spans


`zodiac` is a simple gem for getting a zodiac sign from a given date of birth. It extends `Time`, `Date` and `DateTime` objects with a `#zodiac_sign` method and can also extend `ActiveRecord::Base` with several instance (delegated to some date attribute of the model object) and class methods (allowing you to search for objects with a certain zodiac sign)

## Installation

``` bash
gem install zodiac
```

Or, if you want to extend your rails app, add the following to the `Gemfile`:

``` ruby
gem 'zodiac'
```

and run `bundle install`.

## Usage

### Time/Date/DateTime usage

``` ruby
require 'zodiac'
Time.now.zodiac_sign                  # => "Aries"
require 'date'
Date.new(2011, 1, 1).zodiac_sign      # => "Capricorn"
DateTime.new(2011, 4, 30).zodiac_sign # => "Taurus"
```

`#zodiac_sign` returns values using `I18n` with "zodiac.#{sign}" path, so if you want your own translations, you can put them in your locale with keys like `zodiac.aries`, `zodiac.taurus` etc. See examples [here](http://github.com/7even/zodiac/blob/master/lib/locales/en.yml).

There are also predicate methods which return `true` if the date is matching the specified zodiac sign (and `false` otherwise).

``` ruby
Date.new(1989, 2, 26).pisces? # => true
Time.gm(1978, 7, 12).gemini?  # => false
```
