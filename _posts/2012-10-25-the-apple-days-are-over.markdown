---
title: The Apple Days are over
layout: post
---

{{ page.title }}
----------------
----------------

I originally began this post on March, 19th and never finished it. 

The reason was that I got lost in a long story about when I started with Linux, moved to Unix, ended up with Apple
and then finally found my way back to Linux... 
Today I finished that post to get it out of my mind. It still is that long storu though. But who knows if there isn't
somebody who is interested in it. 

tl;dr
----

How did I end up with Mac OS X anyways?
---------------------------------------

I came a long way: Microsoft MS-DOS, Microsoft Windows, SuSE Linux, Debian Linux, FreeBSD and finally Mac OS X.
Not included the other Linux distributions I tried once in a while and the Commodore Basic V2.

At college I used most of my free time (and the other time, too) to learn about and try things on Linux. Starting with
full desktop environments like KDE and [Gnome](http://www.gnome.org/")[^2] I more and more learned to love the power of 
the Shell and the tools available for it. So when I opted out of college in 2003 I read my mails with 
[mutt](http://www.mutt.org/), read the news with [tin](http://www.tin.org/), did some serious chatting with 
[irssi](http://www.irssi.org/) and hacked code in [vim](http://www.vim.org/).
My favorite windowmanager at that time was [Openbox](http://openbox.org/), because it was incredibly fast. 
And it did what I needed it for:
managing my program windows. I had Openbox configured to be fully controlable with the keyboard. I only touched the mouse 
when I surfed the interwebs[^3].

I started my new job as system administrator and software developer and still was hoping to be able to stick to my tools. 
But they gave me an Apple PowerBook G3 ([Pismo](http://en.wikipedia.org/wiki/File:Powerbook_g3_pismo.jpg)) and told me that 
everybody should use Mac OS X[^4] because of ease of use and compatibility.

Compatibility ment, that I had to use Apple Mail for office mails and [BBedit](http://www.barebones.com/products/bbedit/) for my code. 
There was almost a new tool for
everything. That was the reason I installed Openbox on the Mac and used it within the X11 environment for my private stuff.
I now had two parallel systems on the Mac: the Mac OS X world and a world made up from tarballs and lots of compilation
cycles. It was exhausting, but I tried as hard as possible to keep the tools I mastered over the years. 

But because I had to switch between OS X and X11 it did not feel right. And I did not like the compile-almost-everything
strategy I had chosen. I tried [Macports](http://www.macports.org) and [fink](http://www.finkproject.org/) to install 
the necessary libraries for other things I wanted to install.
It helped to speed up installations, but did not make it less complex to know later, what has been added to the system 
by which method or tool. So I erased the whole disk on the Pismo and installed [NetBSD](http://www.netbsd.org/)[^5]. 

I should have known the reaction of the management, when I came back to office showing around the result of the last
weekend's work: _nyet!_

I installed Mac OS X ("Panther" by that time) again and build vim from the sources. I resigned and from that day on I
primarily used what OS X had to offer.

And I got used to it over the years.


Why did I spent my own money on Apple Hardware later?
-----------------------------------------------------

While working in my frist job I got some hardware upgrades over the years. The Powerbook Pismo was very slow with newer
versions of Mac OS X, so I got the latest and fastest iBook. Which I really enjoyed: it was really fast (at that time)
and the 12" version was very handy but still useable.[^6]
When the iBook died I got a MacBook Pro. One of those that still looked like the late Powerbooks. I had left the Power-PC
behind me finally. And besides the benefits of being able to run virtual machines on my new hardware, I now was able to
watch videos on YouTube, too.

When I left the job I had to give the MacBook back. In the last 5 years I really got familiar with the operating system
and even though there were not all the great console tools available out of the box, most of the applications available
for the Mac had evolved to be not so dramatically feature-less like a few years ago.
And I did not really work on the MacBook at that time anymore. The last year in that job I worked at customer sides, so I
often had to use their hardware or I just needed the Terminal application of OS X to get to work.

So when I quit the job I had to buy a new MacBook Pro. Because it was faster, lighter and shinier than the other laptops
I knew. And I had the idea, that I might do something useful with it, when driving to my new job.

But I didn't.


Time to become productive again!
--------------------------------

At the new job I had to use Windows XP at the office. So this did not feel like home at all. But I already had been able to
lower my expectations on productive tools once...

A couple of months later I bought a Lenovo T60 Thinkpad to install FreeBSD on it. I can't exactly remember what has been the
thought behind all this. Maybe I tried to get back the good old system I used to have before I started to work and had lots
of time to play around with tools and languages.... I really don't know. But problem was that FreeBSD did not work too well
on the Thinkpad. I was able to install everything I needed and play a bit with the Haskell based Xmonad windowmanager. The
main reason to get rid of the Thinkpad again was, that I wasn't able to get the powermanagement work properly.

Another reason was the fact that I tried to make a laptop work for every day
usage that was less powerfull, heavier and with an awfull screen resolution
while having the shiny MacBook Pro lying around at home. It turned out that
running FreeBSD on old hardware wasn't the solution to get the feeling of being
productive and creative again. I had the chance to take a new job. And I did.
Even though the old job was pretty damn safe.

And lots of things changed:
- when I arrived I had a Linux workstation waiting for me
- I began using the awesome tiling windowmanager[^7]
- vim, my favorite editor was available again

Now I had a job where I had the base for a hacker's life again. Now what? - It turned out that the job really had lots of
cool projects waiting and lots of new stuff to learn and do. But this is not the story about that.


Good bye, OS X.
--------------

Because I now used Linux again the whole day it began to feel weird when I went home and had to use OS X again.
I started hacking on a private Ruby project and had to admit that developing with up to date versions is not ment
to be on a Mac. You always have to install the version you really need besides the version Apple had in mind for you.
And the problem is, that Apple only seems to update Java once in a while. 

Then you begin to use tools like Homebrew. A few years ago you used fink or macports, now Homebrew is the standard to easily
install standard unix tools in newer versions or at all. Except when it does not work and that happened a lot...

Then I stumbled upon ["Why OS X just doesn't cut it"](http://cloudhead.io/2011/04/18/why-osx-doesnt-cut-it/) and started to
look for a Linux distribution that might be installed on my meanwhile old Macbook Pro (late 2008). First I took the easy way out
and installed Linux Mint 12. I had Ubuntu at work, so it felt almost the same and I was able to install into a complete Gnome 3 desktop
environment which was able to recognize all hardware. The good thing was that I was able to install everything I had at the office, too.

But that changed soon and I moved from Mint to Arch. Because it's cooler, you know? Just kidding. The more time I spent in the community
again, I came across more and more stuff I wanted to test myself and I had to admit that Ubuntu/Mint still is limited when it comes to
up to date software[^8] and I don't want to install to much manually. Except for vim.

Today I removed all of my TimeCapsule backups on the NAS. Good bye, Apple, I won't come back.


[^2]: I downloaded the whole sources tarballs of Gnome v1.0 back in 1999, which
made my parents think about spending the rent for me living at a students home
in college instead of having me around and paying for the internet bills...
[^3]: I never got used to terminal web browsers like lynx, w3m or elinks though.
[^4]: Mac OS X 10.2 "Jaguar"
[^5]: NetBSD was the only Unix/Linux operation system with serious support for Power-PC.
[^6]: I studied half-time back then and was allowed to use the iBook outside the office, too. It was nice to always carry
it around. But I have to admit that using Eclipse on 1024x768 was a pain. More pain than Eclipse is by itself.
[^7]: I never forgot about the comfort of a tiling windowmanager since I used Xmonad on the Thinkpad for a few weeks.
[^8]: Not to speak about removing Sun Java (Oracle, even) from the repositories and crap like that
