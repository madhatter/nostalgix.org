---
layout: post
title: DWM is Awesome (for now)
tags:
- archlinux
- linux
- dwm
- awesome
- wmfs2
- windowmanager
comments: true
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
noticeable at all. Others were even noticing performance issues and crashes.

So it was about time for me to take a look for a new windowmanager. A tiling one 
of course.  
I have been using [Xmonad](http://xmonad.org/) a couple of years ago when I
wanted to use FreeBSD on an old IBM Thinkpad T60. I did like it back then, but I
had some problems with fullscreen mode for watching videos. And a huge problem
is the configuration file written in Haskell. I remember hacking a bit Haskell
back then, but even though reading and changing the config was a PITA.

I remembered some other windowmanagers I read or heard about or even gave a try
yet some time ago:
[monsterwm](http://github.com/c00kiemon5ter/monsterwm),
[herbstluftwm](http://wwwcip.cs.fau.de/~re06huxa/herbstluftwm/),
[ratpoison](http://www.nongnu.org/ratpoison/)[^1],
[wmfs2](http://wmfs.info/)[^2]
and dwm[^3].  
I went with dwm. I can't exactly say why, but maybe it was because I kinda liked
the idea that you have to compile dwm when you want to change something. Arch
makes it very easy to compile your own versions with
[ABS](https://wiki.archlinux.org/index.php/Abs). I just had to tweak the
PKGBUILD file a bit, configure dwm to my personal needs in the config.h
header file and call `makepkg`.[^4]  
That's the basic version. If you want to have things that dwm does not offer to
you by default your can patch the source code yourself or try to find somebody
who already did that. The only problem might be that you can't apply lots of
patches you find here and there above each other. But as you already have the
lines of code that have to be added or changed you can patch it manually and
then create your very own patch file(s). Then you are able to patch dwm
everytime from vanilla source again when you change the header file.  
Sounds difficult? You'll get used to it.

I don't know if I am already done with my [dwm
configuration](https://github.com/madhatter/dwm) yet, but at the moment I don't
miss something special. And when I thought that wmfs2 might be a bit too
spartan, I now think that you don't need much more than that what dwm or wmfs2
have to offer. Most of the time I only used two tiling modes in awesome anyway.  
I haven't found something like widgets, but at the moment I am very happy with
[conky](http://conky.sourceforge.net/) and I already had something ready from my
days with wmfs2...

For now I am very happy with dwm. But I am pretty sure it won't be the last
windowmanager I install. What is it about this *Unity* everbody is talking about
lately...?

**Update**  
I almost forgot to list the patches I have applied at the moment:  
* statuscolors
* pertag
* scratchpad-stay
* cflags
* single_window_no_border
* centered-floating
* save_floats

More information on those patches can be found on [dwm's homepage](http://dwm.suckless.org/patches/).

[^1]: I don't know for sure, but I think I even had ratpoison running for a few
days back in 2002. But I think I haven't been ready for a tiling windowmanager
back then.
[^2]: I used wmfs2 a few months ago for a week or so. But compared to awesome (at
that time) I missed a few things and found it too minimalistic.
[^3]: The first time I came across dwm must have been when I was looking for
[dwb](http://portix.bitbucket.org/dwb/) some time ago. A nice browser you should
take a look at if you haven't already.
[^4]: For more information on how to install dwm via the Arch Build System take
a sharp look at the [wiki](https://wiki.archlinux.org/index.php/Dwm).

