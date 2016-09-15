
PKG_REVISION = ".0"

require 'simplecov'
task :coverage do
  SimpleCov.start
  SimpleCov.command_name 'Unit Tests'
  Rake::Task[:test].execute
end

$:.unshift "lib" if File.directory? "lib"
require 'rcodetools'
require 'rake/testtask'
RCT_VERSION  = Rcodetools::VERSION

desc "Run the unit tests in pure-Ruby mode ."
Rake::TestTask.new(:test) do |t|
  t.test_files = FileList['test/test*.rb']
  t.verbose = true
end

task :default => :test

desc "install by setup.rb"
task :install do
  sh "sudo ruby setup.rb install"
end

desc "release in rubyforge"
task :release do
  Dir.mkdir('pkg') unless FileTest.exist?('pkg')
  sh "gem build rcodetools"
  sh "mv rcodetools-#{RCT_VERSION}.gem pkg"
  sh "gem push pkg/rcodetools-#{RCT_VERSION}.gem"
end

# vim: set sw=2 ft=ruby:
