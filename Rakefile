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
  #Rake::Task["sitemap:build"].invoke
end

desc 'Build and deploy'
task :deploy => :build do
  sh 'rsync -rtzh --progress --delete _site/ deployer@nostalgix.org:/var/customers/webs/arvid/www/'
  Rake::Task[":ping"].invoke
end

desc 'Build and deploy locally'
task :local => :build do
  sh 'rsync -rtzh --progress --delete  _site/ /usr/share/nginx/html/blog/'
end

desc 'Notify Google of the new sitemap'
task :ping do
  require 'net/http'
  require 'uri'
  Net::HTTP.get(
      'www.google.com',
      '/webmasters/tools/ping?sitemap=' +
      URI.escape('http://nostalgix.org/sitemap.xml')
  )
end

def jekyll(opts = '')
    sh 'rm -rf _site'
      sh 'jekyll ' + opts
end

