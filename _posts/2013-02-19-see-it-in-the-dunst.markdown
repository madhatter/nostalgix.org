---
layout: post
title: See It In The Dunst
tags:
- archlinux
- linux
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
[awesome](http://awesome.naquadah.org) days were the `nm-applet`, `dropbox` and
sometimes the `pidgin` notificiation icon.

Only I few days later I noticed that that pidgin icon was the only thing I
really was missing because I ignored all jabber messages from my co-workers the
whole day.  
But would it be a good idea to add another patch just for one icon?

No. So I have been looking for alternatives and ended up with installing
[dunst](https://github.com/knopwob/dunst), a *dmenu-ish notification
daemon*.[^2] The only problem was, that `pidgin` did not seem to like `dunst` at
all and I haven't been able to get any notifications from it. This was the last
reason necessary to get rid of `pidgin` at all and move to some other client
instead. For my private instant messaging pleasures I have been using
[bitlbee](http://www.bitlbee.org) for a while now to combine it with my IRC
client[^3].  
I couldn't use that environment though, because it's located on a remote host
and it would be a lot more difficult to get local notifications from there.

As I already know irssi I installed [weechat](http://www.weechat.org/) on my
workstation to check it out for this *project*. But it seemed that there were no
scripts available that worked with `libnotify`[^4], so I wrote one myself. In
Ruby, of course.

<!-- <script src="https://gist.github.com/madhatter/4986925.js"></script> -->
{% render_gist https://gist.github.com/raw/4986925/1898b15049f2787250f5892693eb5f1d28e04799/notify.rb RubyLexer %}

The script does nothing special, but notifies me about mentions of my nickname
in a channel or a query.

[^1]: http://en.wikipedia.org/wiki/Taskbar

[^2]: To be honest I don't see what is so *dmenu-ish* about it. If you do,
    please let me know.

[^3]: irssi: http://www.irssi.org

[^4]: https://wiki.archlinux.org/index.php/Libnotify

