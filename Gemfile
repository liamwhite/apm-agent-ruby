# frozen_string_literal: true

source 'https://rubygems.org'

git_source(:github) { |repo_name| "https://github.com/#{repo_name}" }

gemspec

gem 'rack-test'
gem 'rspec'
gem 'rspec-its'
gem 'rubocop', require: nil
gem 'timecop'
gem 'webmock'

gem 'elasticsearch', require: nil
gem 'fakeredis', require: nil
gem 'faraday', require: nil
gem 'json-schema', require: nil
gem 'mongo', require: nil
gem 'opentracing', require: nil
gem 'rake', require: nil
gem 'sequel', require: nil
gem 'sidekiq', require: nil
gem 'simplecov', require: false, group: :test
gem 'simplecov-cobertura', require: false, group: :test
gem 'yard', require: nil
gem 'yarjuf'

if RUBY_PLATFORM == 'java'
  gem 'jdbc-sqlite3'
else
  gem 'sqlite3'
end

framework, *version = ENV.fetch('FRAMEWORK', 'rails').split('-')
version = version.join('-')

case version
when 'master'
  gem framework, github: "#{framework}/#{framework}"
when /.+/
  gem framework, "~> #{version}.0"
else
  gem framework
end

gem 'activerecord-jdbcsqlite3-adapter', platform: :jruby

unless version =~ /^(master|6)/
  gem 'delayed_job', require: nil
end

group :bench do
  gem 'ruby-prof', require: nil, platforms: %i[ruby]
  gem 'stackprof', require: nil, platforms: %i[ruby]
end
