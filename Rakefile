require "bundler/gem_tasks"
require "rake/testtask"

require 'bundler'
Bundler.require

Rake::TestTask.new(:test) do |t|
  t.libs << "test"
  t.libs << "lib"
  t.test_files = FileList["test/**/test_*.rb"]
end

task :default => :test