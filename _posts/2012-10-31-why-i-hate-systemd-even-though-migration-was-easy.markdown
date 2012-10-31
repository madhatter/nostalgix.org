---
layout: post
title: Why I hate systemd even though migration was easy
tags:
- archlinux
- personal
- systemd
---

{{ page.title }}
----------------
----------------

I finally moved my [Arch](http://www.archlinux.org/) to
[Systemd](https://wiki.archlinux.org/index.php/Systemd) because in the last few
days I had the feeling that if I won't do it now I will run into serious
trouble.

I have to admit, that I have never been a big fan of the movement to Systemd.
[Initscripts](https://wiki.archlinux.org/index.php/Initscripts) was simple. It
worked well for me and never had complaints about it. So why move to something
else? And I had the feeling that Systemd is just the new sow that gets driven
through the village (*german saying*).

Okay, but I don't make the decisions and there is no opt-out from Systemd. So I
sat down last night and went through the three steps of migration as described
in the [wiki](https://wiki.archlinux.org/index.php/Systemd). I rebooted every
now and then and made sure that I did not break anything. And today my MacBook
Pro is running a initscripts free Arch Linux. The only problem was the
[pommed](https://wiki.archlinux.org/index.php/MacBookPro#Pommed) daemon, which
had no real systemd unit and was relying on Systemd's initscript compatibility.
But I found a light version in the
[AUR](https://aur.archlinux.org/packages.php?ID=58472) that also had the
missing units. Nice. Took only about an hour and I am done.

But today I noticed that
[pm-suspend](https://wiki.archlinux.org/index.php/pm-utils) triggered by acpid
did not work too well anymore.  Or better: suspending worked as usual, but then
waking up again it seemed that now Systemd's own powermanagement tools kicked
in and send the book back to sleep again. I now had to wake my laptop twice
(now more akin to me, but not what I had in mind). I disabled the acpid unit
again with no effect, because I missed the acpid.socket, which I never explicitly
enabled. Until I noticed this I just removed the lines in the `handler.sh` file.

And now what? All done? I am afraid not. There probably will turn up other issues
I would not have when I would be using initscripts again. And that is what bothers
me most. I have to take care of problems I did not get, because *I* wanted to change
my system. I don't like spending my free time on all that.
