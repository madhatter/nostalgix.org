---
date: '2011-09-20 22:11:16'
layout: post
slug: deploy-to-heroku
status: publish
title: Deploy to Heroku
wordpress_id: '32'
tags:
- deployment
- github
- heroku
- rails
- ruby
---

{{ page.title }}
----------------
----------------

A team mate told me about [Heroku](http://heroku.com/) today, when I was bashing my buggy hosting.

At the moment I am playing around with Ruby on Rails and I was looking forward to it for a while. This was the initial reason to change my hosting and move to a host who claimed to offer RoR services. But then I noticed that just deploying a very small project did not work too well.

I created a rails project

{% highlight powershell %}    
$ rails new blog
$ cd blog
$ rails generate scaffold post title:string body:text
$ rake db:migrate
{% endhighlight %}

Then I initialized git and commited it to github and heroku.

    
{% highlight powershell %}    
$ git init
$ git add .
$ git commit -m "Initial commit"
$ git add origin git@github.com:madhatter/blog.git
$ git push -u origin master

$ heroku create
$ git push -u heroku master
{% endhighlight %}


This went well so far. But the final step did not work that well:

    
{% highlight powershell %}    
$ heroku rake db:migrate
rake aborted!
Please install the postgresql adapter: `gem install 
activerecord-postgresql-adapter` (pg is not part of the bundle. Add it to Gemfile.)

Tasks: TOP => db:migrate => db:load_config
(See full trace by running task with --trace)
{% endhighlight %}


First problem, there is no gem like 'activerecord-postgresql-adapter'.

So I installed the regular pg gem which needed postgresql to install without errors (not too remarkable, eh).

    
{% highlight powershell %}    
$ brew install postgresql
$ gem install pg
{% endhighlight %}


I found a few hints on stackoverflow where lots of people seemed to have similar issues and so I went on to add the pg gem to the Gemfile and use bundle afterwards.

    
{% highlight ruby %}    
group :production do
    # Only gems for heroku
    gem 'therubyracer-heroku', '0.8.1.pre3'
    gem 'pg'
end
{% endhighlight %}

{% highlight powershell %}    
$ bundle install --without production
{% endhighlight %}


But while moving from stackoverflow to google to heroku to the manpages I missed one very important step. I have been trying to call

    
{% highlight powershell %}    
$ heroku rake db:migrate
{% endhighlight %}


after doing some changes, but with no luck. Then tried something else and again tried to migrate heroku.

Of course you have to commit the Gemfile changes and push 'em to heroku. (Doh!)

    
{% highlight powershell %}    
$ git commit -m "Adding the pg gem to the Gemfile."
$ git push -u heroku master
{% endhighlight %}


And then the migrate will work with no errors.
