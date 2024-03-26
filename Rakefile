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

desc 'Build site with Jekyll local with drafts'
task :build_local do
  jekyll '--drafts'
end

desc 'Build and deploy'
task :deploy => :build do
  sh 'rsync -rtzhO --progress --delete _site/ deployer@nostalgix.org:/var/www/test'
  Rake::Task[:notify].invoke
end

desc 'Build and deploy locally'
task :local => :build_local do
  sh 'rsync -rtzh --progress --delete  _site/ $HOME/blog/'
end

task :notify => ["notify:google", "notify:bing", "notify:feedburner"]
desc "Notify various services that the site has been updated"
namespace :notify do
  domain = "nostalgix.org"
  sitemap = "/sitemap.xml"

  desc "Notify Google of updated sitemap.xml"
  task :google do
    begin
      require 'net/http'
      require 'cgi'
      puts "==> Notifying Google that #{domain} has been updated..."
      Net::HTTP.get('www.google.com', '/ping?sitemap=' + CGI.escape("https://#{domain}#{sitemap}"))
    rescue LoadError
      puts "! Could not ping Google, because Net::HTTP or URI could not be found."
    end
  end

  desc "Notify Bing of updated sitemap.xml"
  task :bing do
    begin
      require 'net/http'
      require 'cgi'
      puts "==> Notifying Bing that #{domain} has been updated..."
      Net::HTTP.get('www.bing.com', '/indexnow?url=' + CGI.escape("https://#{domain}#{sitemap}"))
    rescue LoadError
      puts "! Could not ping Bing, because Net::HTTP or URI could not be found."
    end
  end

  desc "Notify Feedburner of updated sitemap.xml"
  task :feedburner do
    begin
      require 'net/http'
      require 'cgi'
      puts "==> Notifying Feedburner that #{domain} has been updated..."
      Net::HTTP.get('feedburner.google.com', '/fb/a/pingSubmit?bloglink=' + CGI.escape("https://#{domain}#{sitemap}"))
    rescue LoadError
      puts "! Could not ping Feedburner, because Net::HTTP or URI could not be found."
    end
  end
end

def jekyll(opts = '')
#  sh 'rm -rf _site'
  sh 'jekyll build ' + opts
end
