require 'cane/rake_task'

desc "Run code sanity checks"
Cane::RakeTask.new(:sanity) do |cane|
  cane.canefile = '.cane'
end

desc "Build the gem"
task :build => :sanity do
  sh 'gem', 'build', *Dir['*.gemspec']
end

desc "Cleans unneeded or old files"
task :clean do
  Dir['{*.gem,doc}'].each do |f|
    rm_rf f
  end
end

desc "Install locally"
task :install => [:clean, :build] do
  sh 'gem', 'install', *Dir['*.gem']
end

desc "Create the documentation for the project"
task :doc do
  sh 'yard'
end
