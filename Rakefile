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
  sh 'rsync -rtzhO --progress --delete _site/ deployer@nostalgix.org:/var/customers/webs/arvid/www/'
  Rake::Task["sitemap:ping"].invoke
end

desc 'Build and deploy locally'
task :local => :build do
  sh 'rsync -rtzh --progress --delete  _site/ /usr/share/nginx/html/blog/'
end

namespace :sitemap do
  desc 'Notify Google of the new sitemap'
  task :ping do
    require 'net/http'
    require 'uri'
    require "net/http"
    uri = "http://nostalgix.org"

    params = "/ping/?title=&blogurl=#{URI.escape(uri)}&rssurl=&chk_weblogscom=on&chk_blogs=on&chk_technorati=on&chk_feedburner=on&chk_syndic8=on&chk_newsgator=on&chk_myyahoo=on&chk_pubsubcom=on&chk_blogdigger=on&chk_blogstreet=on&chk_moreover=on&chk_weblogalot=on&chk_icerocket=on&chk_newsisfree=on&chk_topicexchange=on"
    puts "pinging pingomatic"
    Net::HTTP.get("pingomatic.com", params)

    puts "pinging google"
    Net::HTTP.get("www.google.com" , "/webmasters/tools/ping?sitemap=" + URI.escape(uri+"/sitemap.xml"))

    puts "pinging feedburner"
    Net::HTTP.get("feedburner.google.com", "/fb/a/pingSubmit?bloglink=#{URI.escape(uri)}")
  end
end

def jekyll(opts = '')
  sh 'rm -rf _site'
  sh 'jekyll build' + opts
end
