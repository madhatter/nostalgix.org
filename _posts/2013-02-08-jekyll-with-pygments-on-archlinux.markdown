---
layout: post
title: Jekyll with Pygments on Arch Linux
tags:
- archlinux
- jekyll
- pygments
- python
- github
comments: true
---

{{ page.title }}
----------------
----------------

As I am trying to blog more I came accross [Pygments](http://pygments.org) again and wanted to give
it a try. But I had to notice that Jekyll failed to highlight anything, because
of Arch Linux using Python3 as default (`/usr/bin/python` is linked to
`/usr/bin/python3`).  
Lots of googling later I found out, that it isn't exactly Jekyll's fault, but a
problem with the [pygments.rb gem](https://github.com/tmm1/pygments.rb). There
already is a [pull request](https://github.com/tmm1/pygments.rb/pull/59) for this
[issue](https://github.com/tmm1/pygments.rb/issues/49) which has been opened 3
months ago.  
It really is easy to fix though, but I guess it might cause issues on other
Linux distributions which have no Python 3 at all and therefore no `python2`
command available.  
For now I went to the gem's installation path and changed `mentos.py` manually:

{% highlight bash %}
#!/usr/bin/env python2
{% endhighlight %}

Quick and **very** dirty. A better solution probably would be to fork the gem's
repository, patch it to your needs and install that one.

