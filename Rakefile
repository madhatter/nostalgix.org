begin
    require 'rubygems'
      require 'bundler'
rescue LoadError
    raise "Could not load the bundler gem. Install it with `gem install bundler`."
end

begin
    Bundler.setup
rescue Bundler::GemNotFound
    raise RuntimeError, "Bundler couldn't find some gems. Did you run `bundle install`?"
end

task :default => :build

desc 'Build site with Jekyll'
task :build do
    jekyll
end

desc 'Build and deploy'
task :deploy => :build do
    sh 'rsync -rtzh --progress --delete _site/ deployer@nostalgix.org:/var/customers/webs/arvid/www/'
end

def jekyll(opts = '')
    sh 'rm -rf _site'
      sh 'jekyll ' + opts
end

