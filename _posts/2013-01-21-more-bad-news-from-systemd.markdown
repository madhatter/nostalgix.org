---
layout: post
title: More bad news from systemd
tags:
- systemd
- archlinux
- linux
- powermanagement
comments: true
---

{{ page.title }}
----------------
----------------

The last weeks have been horrible. Every now and then (but within 2 days for sure)
my Macbook did not recover from suspending very well. I wasn't able to figure out
what went wrong exactly, but something seemed to fail when setting the harddisk asleep.
The terrible result was that the root partition was mounted read-only when the book 
woke up again. Because I only have /boot and /home on own partitions and /var is part of
the / partition I wasn't able to remount it read-write again.
So I had to reboot often and do manual filesystem checks every two days at last.

A few days ago I sat down and tried to figure out when those problems might have happened 
for the first time. And then I realized that it probably began with the upgrade to systemd.
I had issues back then with the supsend because acpid and systemd wanted to take care of it. 
The result was that acpid called `pm-suspend` exactly when systemd woke the Macbook up again and
it never woke up at all.
So I edited `/etc/systemd/login.d` to set `HandleLidSwitch` to `ignore` and made the `handler.sh` 
in `/etc/acpi` handle the supsend by `pm-suspend` again.
