---
layout: post
title: Howto fix RVM path issues
tags:
- archlinux
- rvm
- ruby
- troubleshooting
lang: en
comments: true
---

{{ page.title }}
----------------
----------------

I had some trouble with [rvm](https://rvm_io.global.ssl.fastly.net/) lately on
the
[Odroid](http://www.hardkernel.com/main/products/prdt_info.php?g_code=G145457216438)
setup which took me some time to figure it out. I had no idea what might be
wrong because I have been using rvm on all my setups for the last 5 years
without any issues. And as I have all my
[dotfiles](https://github.com/madhatter/dotfiles) stored in a GitHub repository
I was quite sure, that I had a working zshrc.

But when I logged in I noticed that I was always falling back to system's ruby
even though I had set the rvm ruby version as default. And when I tried to
re-set the ruby as default again I got the following warning from rvm:

> Warning! PATH is not properly set up, '$HOME/.rvm/gems/ruby-2.1.5/bin'
is not at first place, usually this is caused by shell initialization files -
check them for 'PATH=...' entries, it might also help to re-add RVM to your
dotfiles: 'rvm get stable --auto-dotfiles', to fix temporarily in this shell
session run: 'rvm use ruby-2.1.5'.

It took quite some while and lots of useless googling to find the reason: I made
the mistake to install rvm for the root user, too. I never did that before (and
I probably never will ever again) and did not know that rvm installs
/etc/profile.d/rvm.sh if it has root rights.  
Because this zlogin was evaluated first and I later moved parts of the PATH in
my local ~/.zshrc becore finally calling the rvm scripts again, rvm got messed
up and did not work correctly.
After deleting /etc/profile.d/rvm.sh this was fixed.  
