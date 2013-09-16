---
layout: post
title: vim - 12 years and counting
tags:
- vim
- linux
- debian
- archlinux
- editor wars
comments: true
---

{{ page.title }}
----------------
----------------

Everybody is telling you right now, how they configured vim and which plugins
they are using. At the moment you can get the idea, that vim becomes one of the
hippest editors and people want to show off by hanging their `.vimrc` out. Maybe
the girls like that.  
So, [here](https://github.com/madhatter/vim) is the repository with my vim
configuration, knock yourself out... Just kidding. I don't know if I have build
a `.vimrc` which makes a grown man cry and it also is pretty well documented,
but I think this is not what it is about.

I came to vim about 12 years ago in 2001 and Debian Potato was the distribution
of my choice back then. If I remember correctly it was vim version 5.6 or 5.7.
Code folding wasn't available and came with vim 6.0. Can you imagine that?  
I remember trying emacs before, but I had terrible issues with the keybindings
(still have) and used gEdit or something like that since then. Until a room-mate
told me about vim and got me hooked.[^1]  But things were different in these days:
the internet was made from wood and there weren't too many websites available
that told you how to configure vim *best*. You mostly had to figure out that by
yourself and it wasn't about adding lots of plugins, but change one or two
settings here and there. You were busy enough to configure vim's core
functionalities but adding lots of plugins. And let's be realistic, there hasn't
been any git back then that you might wanted to call from your editor.[^2]

Of course, it took me some time to get used to vim's commands, but it got much
better when I stopped using different editors from time to time and instead used
vim for everything: writing emails, taking notes, writing news posts, coding,
...  you name it. And that is what bothers me about lots of articles I read in
the last few months: telling people how hard it is to get used to vim! If you
use it regularly you will get used to it very fast. The only thing you should
keep in mind is that you might have to take some extra time to figure out how you
can do things faster in vim when you get the feeling that you are using to many
keystrokes to do something. There *is* a better way.  
I think it's the same problem when people switch from Windows or OS X to Linux
or Unix or whatever: you have to use it for everything and don't ignore when
something does not seem to work as well as it should.  
And it might not be the best idea to copy whole vim configurations from others
for a starting point. Just read them and look up those things that sound
interesting in vim's [help](http://vimdoc.sourceforge.net/htmldoc/) and
configure them to your needs then.

I think the best tip I can give you from my perspective is to make yourself
comfortable. Vim is an editor that can do lots for you, but you have to know
what you want first.  
And maybe vim isn't the right editor for you if you don't feel comfortable with
it. Don't try to use it just because so many people are writing about it at the
moment. There are lots of other editors available that might suit you better. I
have a colleague who uses emacs. And he likes using it. Nobody forces him to do
so. I can't understand that, but people are different.

And at last I have to admit, that I don't use vim for everyting anymore today. I
spent months by trying to code Java with it, but I never made vim such easy and
helpful as a full-featured Java-IDE like Netbeans.[^3] And it makes pair-programming
so much easier with workmates.  

You should not be too dogmatic about these things.

[^1]: He also got me hooked on mutt and slrn. And it's a shame that he does not
	use anything of these anymore...

[^2]: I know people you use IDEs like eclipse or Netbeans for Java, but execute
	git/mercurial and maven from the command line next to it, because they don't see
	the benefits in using a plugin for their IDE that might not be able to give them
	all the functionality the original tools do.

[^3]: If anybody has the solution for that, I would be happy to hear about it
	though.
