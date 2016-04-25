# FaradayMiddleware::OAuth2Refresh

[![Gem Version](https://badge.fury.io/rb/faraday_middleware-oauth2_refresh.svg)](http://badge.fury.io/rb/faraday_middleware-oauth2_refresh)
[![Build Status](https://img.shields.io/travis/grokify/faraday_middleware-oauth2_refresh/master.svg)](https://travis-ci.org/grokify/faraday_middleware-oauth2_refresh)
[![Code Climate](https://codeclimate.com/github/grokify/faraday_middleware-oauth2_refresh/badges/gpa.svg)](https://codeclimate.com/github/grokify/faraday_middleware-oauth2_refresh)
[![Coverage Status](https://coveralls.io/repos/grokify/faraday_middleware-oauth2_refresh/badge.svg?branch=master)](https://coveralls.io/r/grokify/faraday_middleware-oauth2_refresh?branch=master)
[![Docs](https://img.shields.io/badge/docs-rubydoc-blue.svg)](http://www.rubydoc.info/gems/faraday_middleware-oauth2_refresh/)
[![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/grokify/faraday_middleware-oauth2_refresh/master/LICENSE.txt)

Faraday middleware to manage OAuth token authorization with token refresh.

## Description

This gem is a piece of Faraday middleware that adds OAuth token handling using the [oauth2 gem](https://github.com/intridea/oauth2).

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'faraday_middleware-oauth2_refresh'
```

And then execute:

```sh
$ bundle
```

Or install it yourself as:

```sh
$ gem install faraday_middleware-oauth2_refresh
```

## Usage

```ruby
require 'oauth2'
require 'faraday_middleware/oauth2_refresh'

client = OAuth2::Client.new('my_client_id', 'my_client_secret', site: 'https://example.com' )
token  = client.password.get_token('username', 'password', { headers: { 'Authorization' => 'Basic my_api_key' } })

conn = Faraday.new(url: "http://example.com") do |builder|
  builder.request :oauth2_refresh, token
  builder.adapter Faraday.default_adapter
end

conn.get "/foo" # sends token
```

## Change Log

- **2015-05-31**: 0.0.2
  - Update dependencies
- **2015-05-31**: 0.0.1
  - Initial release

## Links

Project Repo

* https://github.com/grokify/faraday_middleware-oauth2_refresh

## Problems, Comments, Suggestions, Contributions?

Any reports of problems, comments or suggestions are most welcome.

Please report these on [Github](https://github.com/grokify/faraday_middleware-oauth2_refresh)

## License

RingCentral SDK is available under an MIT-style license. See {file:LICENSE.txt} for details.

RingCentral SDK &copy; 2015 by John Wang