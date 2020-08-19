# frozen_string_literal: true

require 'bundler/gem_tasks'
require 'rake/testtask'

require 'bundler'
Bundler.require

Rake::TestTask.new(:test) do |t|
  t.libs << 'test'
  t.libs << 'lib'
  t.test_files = FileList['test/**/test_*.rb']
end

task :add_pending_cops do
  # Only require this if we need it, it takes a while
  require 'rubocop'
  config_store = RuboCop::ConfigStore.new
  config = config_store.for(__dir__)
  pending = config.pending_cops
  next if pending.empty?

  File.open(File.join(__dir__, '.rubocop_pending.yml'), 'a') do |config_file|
    pending.each do |cop|
      config_file.puts
      config_file.puts "#{cop.name}:"
      config_file.puts '  Enabled: true'
    end
  end

  puts "Added #{pending.length} cops to .rubocop_pending.yml"
end

task default: :test
