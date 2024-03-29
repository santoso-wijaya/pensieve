# frozen_string_literal: true

require 'bundler'
require 'rake'
require 'rake/clean'

begin
  Bundler.setup(:default, :development, :jekyll_plugins)
rescue Bundler::BundlerError => e
  $stderr.puts e.message
  $stderr.puts "Run `bundle install` to install missing gems"
  exit e.status_code
end

file 'Gemfile.lock' do |t| sh 'bundle install' end
CLEAN.include 'Gemfile.lock'

# Update the system Node to v18.17.1 (for Cloudflare)
task :npm do |t|
  if not ENV['CLOUDFLARE'] then
    sh 'node -v'
    sh 'npm install -g n'
    sh 'n 18.17.1'
  end
end

# Then invoke npm to install the content of `package.json`
file 'package-lock.json' => [:npm] do |t|
  if not ENV['CLOUDFLARE'] then
    sh 'node -v'
    sh 'npm install'
  end
end
CLEAN.include 'package-lock.json'
CLEAN.include 'node_modules'

rule( %r{assets/js/.*\.rollup\.js$} => ['package-lock.json']) do |t|
  # Invoke a rollup command to resolve JS imports with bare module specifiers.
  sh 'npm run build:js'
end
CLEAN.include 'assets/js/*.rollup.js'

task build: ['Gemfile.lock', 'package-lock.json', 'assets/js/*.rollup.js'] do |t|
  extra_args = ''
  if ENV['CLOUDFLARE_PREVIEW'] then
    extra_args = '--drafts'
  end

  sh "bundle exec jekyll build #{extra_args}"
end
CLEAN.include '.jekyll-cache', '_site'

task default: [:build]

task serve: [:build] do |t|
  sh 'bundle exec jekyll serve --drafts'
end
