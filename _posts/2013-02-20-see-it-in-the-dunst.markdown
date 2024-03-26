---
layout: post
title: See It In The Dunst
tags:
- archlinux
- linux
- dunst
- dwm
- notifications
- scripts
comments: true
---

{{ page.title }}
----------------
----------------

As I mentioned [before]({% post_url 2013-02-06-dwm-is-awesome %}) I am happy using dwm as
my windowmanager for every day. But dwm does not come with a systray[^1] by
default and I felt not like patching one in, because I was wondering why I
should really have one. The only things sitting in the systray back in my
[awesome](http://awesome.naquadah.org) days were the nm-applet, dropbox and
sometimes the pidgin notificiation icon.

Only I few days later I noticed that that pidgin icon was the only thing I
really was missing because I ignored all jabber messages from my co-workers the
whole day.  
But would it be a good idea to add another patch just for one icon?

No. So I have been looking for alternatives and ended up with installing
[dunst](https://github.com/knopwob/dunst), a *dmenu-ish notification
daemon*.[^2] The only problem was, that pidgin did not seem to like dunst at
all and I haven't been able to get any notifications from it. This was the last
reason necessary to get rid of pidgin at all and move to some other client
instead. For my private instant messaging pleasures I have been using
[bitlbee](http://www.bitlbee.org) for a while now to combine it with my IRC
client[^3].  
I couldn't use that environment though, because it's located on a remote host
and it would be a lot more difficult to get local notifications from there.

As I already know irssi I installed [weechat](http://www.weechat.org/) on my
workstation to check it out for this *project*. But it seemed that there were no
scripts available that worked with `libnotify`[^4], so I wrote one myself. In
Ruby, of course.

The script does nothing special, but notifies me about mentions of my nickname
in a channel or a query. And it ignores everything from my nick, because first I
got even noticed about everything I wrote, too.

My
[dunstrc](https://github.com/madhatter/dotfiles/blob/9f21301efae5caf79578a8e33faba6186ffdaa62/.config/dunst/dunstrc)
hasn't been too much changed compared to the default configuration file that
comes with dunst, but I went with the *dwm way* for dunst, too, and build my own
package with a slightly modified `config.h`.[^5]  
Now I am aware of what is happening in the office chat all the time and the nice
thing is, that the dunst notifications follow the focussed monitor. That, and
that the notification window is larger than the icon I used to have with pidgin
makes it much more difficult to miss now.  
I noticed that dropbox makes use of the dunst daemon by default when it is
running, so I somehow replaced the systray icon for dropbox, too.

The only thing I haven't been able to accomplish yet is to make any kind of
application icons appear in dunst. I don't really need this feature, but I have
been wondering what it might look like. But maybe it's just that `libnotify`
does support that and dunst does not.

 

[^1]: http://en.wikipedia.org/wiki/Taskbar

[^2]: To be honest I don't see what is so *dmenu-ish* about it. If you do,
    please let me know.

[^3]: irssi: http://www.irssi.org

[^4]: https://wiki.archlinux.org/index.php/Libnotify

[^5]: I haven't uploaded it anywhere, because I did not patch dunst anyhow, but
    only changed some colors and the font. Maybe I will later, when I am aware
    of what I might tweak in the header file, to make much better use of dunst.

