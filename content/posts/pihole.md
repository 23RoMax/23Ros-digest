---
title: "A life without advertisements - Pihole DNS Adblocker"
date: 2019-09-08T18:04:49+02:00
draft: false
categories: ["general", "life", "lifehacks", "raspberry pi", "projects", "tutorial"]
tags: ["general", "things", "life", "lifehacks", "raspberry pi", "projects", "pihole", "adblocker", "DNS"]
description: "A tutorial in setting up pihole as a DNS level adblocker"
keywords: ["phole", "DNS adblocker", "adblocker", "23Ro", "selfhosted", "raspberry pi"]
---

You have enough of advertisement? Yes, who hasn't... You say you are using an AdBlocker? What if I tell you, there is a much better option than using an AdBlocker. It will safe internet traffic, it will boost loading speeds, and it will give you much more control about everything. Sounds tempting right? 

So, if you have a spare one of these: ![Raspberry Pi](/images/1280px-Raspberry_Pi_Logo.svg@0,25x.png), or even if you don't, check out this tutorial!

And if you don't have a spare [Raspberry Pi](https://en.wikipedia.org/wiki/Raspberry_Pi) lying around, [get one](https://amzn.to/2ZUPEEt), they are 30 Bucks and it's very much worth it! (Check the links below!)

# What is a PiHole?

A [PiHole](https://pi-hole.net/) is a DNS level, network wide, Ad Blocker. It advertises itself as the Black Hole for Internet Advertisements in your Home Network.
It can be hosted locally, or remotely, and it can be deployed directly or in a container. If this sounds complex, trust me, it isn't.

They provide an automated installer, that helps you getting your Raspberry Pi with PiHole up and running. Actually, you don't need to use a Raspi, you can use whatever linux machine you want!

After the installation, you can get informative stats about your consumption and blockages in the PiHole Admin Interface.
<center>
![PiHole Admin Interface Screenshot](/images/pihole-screenshot.PNG)
</center>

# Why a PiHole? I have AdBlock in my Browser extension!

1. PiHole works on DNS level - it blocks all the Ads!
2. It works in all Applications, not only your Browser, but also your Phone, Aps, etc.
3. One installation to rule them all - don't hassle with configuring and installing different AdBlockers across devices! Once your Roter knows your Raspi as DNS provider, you have it in your local network!
4. Anti AdBlock detection won't work!
5. Tracking of client activity built in - Audit your devices, you will be surprised about what they do, even without your fordoing!
6. Beautiful graphs and statistics!
3. It's good for the environment - doesn't create unnecesary trafic and load! 

In our home network of roughly 20 devices, it blocks around 25% to 30% of the total traffic - this means data is not served, servers are not called, execution time of those is 1/3 lower, effectively it should therefore also be good for the environment as less services are requested consuming computing power and thus in the end electricity (ATTENTION: This is a bold statement of mine and one could argue against it - as always....) 

# What do we need?

1. [A Raspberry Pi](https://amzn.to/2ZUPEEt)
Any Raspberry Pi will do, but if you push a lot of bits, bites, and packages through your network like I do, get yourself at least a [Raspi 3](https://amzn.to/2ZUPEEt) or [Raspi 4](https://amzn.to/2ZUg4q8).
Depending on your choice, this will set you back 30 - 70 €.

2. [A SD Card](https://amzn.to/2ZIOq4f)
16 GB is more than plenty.

3. [A USB Power Adapter](https://amzn.to/2ZX5HpH) and a [case](https://amzn.to/34uwcly)
Take the classical Raspberry Pi one, not only does it look good, it's also very practical as you can open the top and the sides. In terms of the power Adapter, depending on your Pi Version, any Phone Charger will do.
Or just go for the full package:  [click me](https://amzn.to/2zYVYQU)
It's 70 € on Amazon, but I'm sure it can be found cheaper.

3. [A linux image](https://www.raspberrypi.org/downloads/raspbian/)
I recomment going for Raspbian Lite, as you don't need all the mumbo jambo and fancy UIs. The command line is all you need!

4. [Pihole itself](https://github.com/pi-hole/pi-hole)
This links to their github, but don't worry, there's an easy way of downloading it without having to ``git clone`` into a repo

# Preparing the Raspberry Pi
First things first, we need to setup the Raspberry Pi.
<center>
![Raspberry Pi](/images/Raspberry_Pi_4_Model_B_-_Side.jpg)
</center>
After dedusting or unpacking your Raspberry Pi, the SD Card, and peripherals, you will need to put a OS on the small thing. This step is probably the most inconvenient of all, as you will need to use a computer of any sort, and afterwards need your computers peripherals like monitor, keyboard, and any type of internet connectivity like ethernet kabel to your router, or wifi, to setup the Raspberry Pi initially.

Now there are several ways of doing so, I recommend the easiest one using a GUI software that a friend of mine used to work on called [Etcher](https://www.balena.io/etcher/).
It's an easy way of installing any downloaded Linux Image on a SD Card and making it bootable, no need to use any DD commands, or other tools like [Rufus](https://rufus.ie/) - which is also a good tool, but only for windows.

## Getting the OS & Software

<center>
![Getting the Linux Image](/images/Raspian_SD-150x150.webp)+![Getting Etcher](/images/etcher.svg)
</center>

1. Download the Raspbian Image (you might use this [link](https://downloads.raspberrypi.org/raspbian_lite_latest)) -- Verify the image with the provided checksum if you whish (not necessary, but helps assuring that there is no malicious version of the OS downloaded)
2. Download Etcher for your OS [here](https://www.balena.io/etcher/)
3. Plugin your microSD card in any card Reader of your PC
4. Open Etcher
5. Select your SD Card
6. Select the Image you want to burn on it (The unzipped ISO file of Step 1)
7. Start and wait for the success message :)

## Plug in your Raspi and do the initial setup

You will need:

1. any Monitor + HDMI Kabel
2. any USB Keyboard (I use my logitech wireless keyboard with its USB Adapter)
3. the prepared SD Card
4. the [Raspberry Pi](https://amzn.to/2ZUPEEt)
5. the [Power Adapter](https://amzn.to/2ZX5HpH)
6. Network (best case, via ethernet cable)

I recommend connecting everything before you connect to power.
The [Raspberry Pi](https://amzn.to/2ZUPEEt) turns on immediately.

It will boot into Raspbian Lite.

<center>
![Raspbian Lite booting](/images/raspberry1.PNG)
</center>
_If you want to see how I did this screenshots without a raspberry pi, check out: [How to emulate ARM processors and run Raspbian on any machine](https://23ro.de/posts/qemu-windows)._

You will be asked to login, on Raspbian Lite the default credentials are:

```shell
login: pi
password: raspberry
```

You will need to change those, it's very dangerous to let the device run on those credentials.
By using the command

```shell
$ passwd
```

you can change it from raspberry to your desired pwd.

Before we can proceed, we need to make sure the Raspberry Pi has access to the internet.
There are several options to do so, the easiest being pinging a widely available resource like the OpenDNS Servers:

```shell
$ ping 208.67.222.222
```

this should return the time in ms that the package needed to travel to the destination (OpenDNS Server) and back to your machine.
If you see something like ``host unreachable`` or ``Timeout`` make sure that your Raspi is thoroughly hooked up to your router!

Now, let's assure that we have the latest packages installed on our Raspberry Pi by running those commands sequentially:

```shell
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```

As we always want to be able to access the device from another PC (we also want to continue the installation process via a secure shell) we have to activate the SSH option in the OS.

#### Option one:

Enter 
```
$ sudo raspi-config
```

Select ``Interfacing options``

Navigate to ``ssh``

press Enter and select Enable ssh server

#### Option two:

This is the pro tip - if you don't have keyboard, HDMI Kabel and Monitor, etc. at hand, you can also touch/echo a empty file on the /boot folder of the sd card named ``ssh``.
It allows for a completely headless setup.

## Install Pi-Hole

Finally the step we have been waiting for, installing Pi-Hole is as easy as running this command:

```
$ curl -sSL https://install.pi-hole.net | bash
```

Just follow the installier which should look like this:
<center>
![PiHole Installer](/images/pi-hole-installer1.png)
</center>

At one point you will be asked to select your upstream DNS provider. I tend to use [OpenDNS](https://use.opendns.com/), or [Cloudflare DNS](https://www.cloudflare.com/learning/dns/what-is-1.1.1.1/), and for several reasons I began avoiding googles DNS (8.8.8.8). But this really is your choice, I recommend doing a bit of reading about the options and why you would choose one over another.
My conclusion draws from experiences I have made over the last years with the given provider. And this might be biased, but as a security and privacy advocate, big data driven cooperations aren't necessarily whom I trust my data the most with.

<center>
![PiHole DNS Selection](/images/pi-hole-dns-provider-selection.png)
</center>

Now you can basically ``enter through`` the installation. It will install lighttpd (a open source webserver), the admin interface etc.
After the installation is done, write down your password to your interface, this is important!

And if you have done everything correctly, you can deploy the raspberry pi securely next to your router.

## Aftercare - making the DNS server available and known to all devices!

Now that the software is setup, we need to make it known to all the devices in the network.
This is fairly simple.

On the last screen of the installation process, we have been told about our IP Adress in the local network. This will become our DNS Server IP that we will need to make locally known.

Now depending on your ISP (Internet service provider) and your router, you will eiter be able to set it via the router or not (Thank you, Vodafone/Kabel Deutschland!). Luckily I'm only using the Vodafone device as a modem in bridge mode. Just navigate to google, search for your routers DNS Settings (they are usually close to the networking or DHCP settings), and set only the IP Adress of your PI as DNS.

This setting will get propogated to all the devices in the network using DHCP to get a IP.

I hope you had fin with this little tutorial!