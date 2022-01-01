desc "default task"
task :default => [:run_server]

desc "run server"
task :run_server do
  system "mkdocs serve"
end

desc "deploy"
task :deploy do
  system "mkdocs gh-deploy"
end