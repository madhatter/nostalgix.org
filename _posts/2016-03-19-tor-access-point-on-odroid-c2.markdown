---
layout: post
title: Howto Setup a Tor Access Point (on an Odroid C2)
tags:
- archlinux
- tor
- howto
- configuration
- linux
- odroid
- microcomputer
lang: en
comments: true
---

{{ page.title }}
----------------
----------------

I got an [Odroid C2](http://www.hardkernel.com/main/products/prdt_info.php) for testing from a work-mate. Because he told me that his initial tests with Ubuntu's alpha version went not too well, I gave [ArchLinux](http://www.golem.de/news/odroid-c2-bastelrechner-mit-2-ghz-und-2-gbyte-ram-1602-119083.html) a try. As I use Arch as my daily driver on non-arm architectures I appreciated that option.  
Installation went smooth, but I had no fancy idea to take the Odroid for a ride.
So I set up a [Tor](https://www.torproject.org/) Access Point for the living room. I already had that in mind for my dated Raspberry Pi, but never was in the mood.  
I came accross a quick [howto in
german](https://tamcore.eu/anonymen-wlan-access-point-mit-archlinux-und-tor-errichten/)
a few months ago and started from there. Because I had some small pitfalls I thought it might be a good idea to write it down.  

First, install the required software
{% highlight powershell %}
# pacman -Sy dnsmasq hostapd tor iptables
{% endhighlight %}

Now configure the dnsmasq service in **/etc/dnsmasq.conf** 
{% highlight powershell %}
interface=wlan0
dhcp-range=10.10.0.25,10.10.0.255,6h
{% endhighlight %}

Next, configure the access point via **/etc/hostapd/hostapd.conf**
{% highlight powershell %}
interface=wlan0
driver=nl80211
ssid=Doors of Passion
country_code=DE
ieee80211d=1
hw_mode=g
ieee80211n=1
channel=9
macaddr_acl=0
{% endhighlight %}

Btw, you probably want to make sure, that the wifi adapter you are using is able to
enter master mode. (iwconfig wlan0 mode master)

We now need a unit file to assign a static ip to the wifi adapter. Create  
**/etc/systemd/system/openwifi.service**
{% highlight powershell %}
[Unit]
Description=Assign static ip to wlan0
Wants=network.target
Before=network.target
BindsTo=sys-subsystem-net-devices-wlan0.device
After=sys-subsystem-net-devices-wlan0.device

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/usr/bin/ip link set dev wlan0 up
ExecStart=/usr/bin/ip addr add 10.10.0.1/24 dev wlan0
ExecStop=/usr/bin/ip addr del 10.10.0.1/24 dev wlan0
ExecStop=/usr/bin/ip link set dev wlan0 down

[Install]
WantedBy=multi-user.target
{% endhighlight %}

And the tor configuration itself in **/etc/tor/torrc**
{% highlight powershell %}
AutomapHostsSuffixes .onion,.exit
AutomapHostsOnResolve 1
TransPort 9040
TransListenAddress 10.10.0.1
DNSPort 53
DNSListenAddress 10.10.0.1
User tor
Log notice syslog
DataDirectory /var/lib/tor
BridgeRelay 0
PublishServerDescriptor 0
{% endhighlight %}

To bind Tor to privileged ports the service must be started as root. We can
modify the tor service by adding
**/etc/systemd/system/tor.service.d/start-as-root.conf** with following content:
{% highlight powershell %}
[Service]
User=root
{% endhighlight %}

And to make all this work together we need to do a few more changes to the system.
We have to enable ip forwarding via sysctl. Create a file like
**/etc/sysctl.d/99-sysctl.conf** with this line
{% highlight powershell %}
net.ipv4.ip_forward=1
{% endhighlight %}

And load this configuration by 
{% highlight powershell %}
sysctl --system
{% endhighlight %}

At last we need some iptables rules to redirect tcp and udp traffic and to route
it from the wlan0 device to eth0:
{% highlight powershell %}
# iptables -t nat -A PREROUTING -i wlan0 -p udp --dport 53 -j REDIRECT --to-ports 53
# iptables -t nat -A PREROUTING -i wlan0 -p tcp --syn -j REDIRECT --to-ports 9040
# iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
# iptables --append FORWARD --in-interface wlan0 -j ACCEPT
# iptables-save > /etc/iptables/iptables.rules
{% endhighlight %}

Let's give it a try and start all services:
{% highlight powershell %}
# systemctl start iptables
# systemctl start openwifi
# systemctl start hostapd
# systemctl start dnsmasq
# systemctl start tor
{% endhighlight %}

And when everything is working you can enable all the services to get them
started after reboot:
{% highlight powershell %}
# systemctl enable dnsmasq hostapd tor openwifi iptables
{% endhighlight %}

If it is not you have to take a further look into it.

On the Odroid C2 it performs very well and if it was any different they did
something very wrong. So I am looking for some other task for the board.

