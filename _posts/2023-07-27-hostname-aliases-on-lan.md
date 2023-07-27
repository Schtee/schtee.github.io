---
title: Hostname Aliases on a LAN In Linux
---

I have a little computer running Linux in my home that I use a home server, running various services such as [FreshRSS](https://freshrss.org/index.html) and [linkding](https://github.com/sissbruecker/linkding). I wanted to setup a bunch of memorable hostnames I could use to point to different services on that machine. This was my journey.

My primary OS is Windows. I'm used to using the machine name (hostname) of the computer to resolve to its local IP address by some sort of magic with no human intervention (apparently this is [NetBIOS](https://en.wikipedia.org/wiki/NetBIOS)? I dunno, I've literally never had to think about it), but that wasn't working for this Linux server PC. After trawling through a bunch of StackExchange posts suggesting the user edit their `hosts` file...on each and every device on their LAN, which is obviously the wrong way around, I found [posts such as this](https://unix.stackexchange.com/a/595377) helpfully indicating that the functionality is offered in zero-conf(iguration) services, such as [mDNS](https://en.wikipedia.org/wiki/Multicast_DNS) and that installing *Avahi* on the Linux machine should broadcast the hostname as `hostname.local` and then be available by name rather than just IP. After a quick

```
sudo apt install avahi-daemon
```

this all worked pretty promptly!

I then got to thinking "wouldn't it be neat if different web services, running on different ports, could be referred to directly by a name?". After some more frantic Googling I found [this amazing post from Andrew Dupont](https://andrewdupont.net/2022/01/27/using-mdns-aliases-within-your-home-network/) walking through basically my exact usecase. The [Python mdns-publisher](https://andrewdupont.net/2022/01/27/using-mdns-aliases-within-your-home-network/#:~:text=SCRIPT%20OPTION%202%3A%20PYTHON%E2%80%99S%20MDNS%E2%80%90PUBLISHER) seemed perfect for what I needed, but unfortunately it bound to the wrong network  interface/IP address and as far as I can see there's no parameter to change that. I ended up using something inspired by [Andrew's clearly less-perfect solution](https://andrewdupont.net/2022/01/27/using-mdns-aliases-within-your-home-network/#:~:text=SCRIPT%20OPTION%201%3A%20AVAHI%E2%80%90PUBLISH) but it totally did the job, basically boiling down to a bunch of calls to

```
avahi-publish -a freshrss.local -R 192.168.1.100 &
avahi-publish -a linkding.local -R 192.168.1.100
```

(etc).

All hostnames were now mapping to the server's IP address correctly, but the port still needed to be specified - this was effectively basic aliases for an IP. The next step in Andrew's article is to [setup nginx proxies](https://andrewdupont.net/2022/01/27/using-mdns-aliases-within-your-home-network/#:~:text=Proxy%20a%20web%20server%20running%20on%20a%20specific%20port). Having seen nginx config syntax before, I didn't really fancy that so looked around for more accessible solutions. I eventually stumbled on [Nginx Proxy Manager](https://github.com/NginxProxyManager/nginx-proxy-manager#quick-setup). I threw together a `docker-composse.yml` based on [their example](https://github.com/NginxProxyManager/nginx-proxy-manager#quick-setup) and the UI was super-legible and looked easy to configure. After making some entries to map the Avahi mDNS names to `http://hostname.local:[port]` everything was working!

![The Nginx Proxy Manager web UI showing some services mapped from server.local to http://server.local:port](/images/2023-07-27-hostname-aliases-on-lan/npm.png)