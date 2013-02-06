---
layout: post
title: DWM is Awesome (for now)
tags:
- archlinux
- linux
- dwm
- awesome
- windowmanager
---

{{ page.title }}
----------------
----------------

Since I moved from OS X back to Linux I have been using the tiling window
manager [awesome](https://awesome.naquadah.org) and most of the time it has been
what it's name let you think it would be.  
A few days ago I moved to [dwm](http://dwm.suckless.org/). Why? And how can it
make such a big difference when awesome is based on a dwm fork?

First of all I never liked the whole [lua](http://www.lua.org/) configuration. I
can't tell exactly why, but to me lua is not very appealing. It starts with the
"--" for comments and leads to the odd habit of [counting from 1 instead of
0](http://lua-users.org/wiki/CountingFromOne).  But the main reason is that
awesome is not awesome when it comes to error handling and logging. If you have
written something wrong in your rc.lua (which is the main configuration file)
awesome will not tell you what exactly is wrong but start with some kind of
default configuration. But there may be times when not even Mod4+Enter will work
to start a terminal.  
The last reason came a couple of weeks ago when I have been forced to update my
configuration to work with the update for version 3.5. The changes have been not
too many, but because I had lots of widgets configured I had to change a lot to
match the new syntax. It took so long to have everything updated that I
downgraded to 3.4.x for some time, because I haven't been in the mood to do the
work.  
And when I was done... what did I get? Right. Nothing. There were no benefits
noticeable at all.
