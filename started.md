---
layout: default
title: Getting Started
nav_order: 2
description: What you will need to set up your own Minecraft server on a Raspberry Pi
---

# Getting Started
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta}

- TOC
{:toc}

---

<!-- may want to add link to YAML parser -->
A small amount of planning and preperation before you get started will save you many hours of frustration later. The choices you make in hardware and software will shape the outcome of your efforts for the better, or for the worst. Please spend a little time reading through the following information before you start to set up your server. If you don't read it now, you might be back to read it later.

---

# What's your favorite flavor of Pi?

If you have found your way here you likely already know what a Raspberry Pi is. It is the most popular of a class of computers known as [single board coputers](https://en.wikipedia.org/wiki/Single-board_computer) or SBC. It is however not the only single board computer in it's class. There are [Orange Pi](http://www.orangepi.org/), [Bananna Pi](https://www.banana-pi.org/), [Rock Pi](https://rockpi.org/) even a [Potato](https://libre.computer/products/s905x/). Indeed the popularity of the Raspberry Pi has spawned a whole industry of campanion hardware and cloned devices. This script is only built and tested on the latest Raspberry Pi. None of these other boards are supported or at this time recommended. The reason for this is simple, the effort required to use one of these other boards does not justify the cause. Simply put these other boards are often poorly documented, poorly supported, there is limited OS availability and even more limited community support. This is not to say any of these products are bad. It's simply that the effort to use one of these SBC's is beyond the scope of this project. Use them at your own risk.

For a modern 1.18+ minecraft server it is highly recommended to use a [Raspberry Pi 4b](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) with 8gb of ram. Yes other versions of the Pi will work and if all you have is a Pi with 4gb it's certainly worth a try to see if the results are acceptable to you. A Pi with 2gb of ram is the lowest I would recommend going. The PiCubed script will not continue installation if less than 1gb of **AVAILABLE** ram is detected. Remember that if your Pi only has 1gb of ram, you will not have 1gb of available ram because some of it is being used by the Pi OS and system.

---

# Which Operating System?

If this is your first time tinkering with a Pi you may not be familiar with the vast array of operating systems available for the Pi. There are everything from fully funtioning Windows like environments to retro gaming platforms. After your choice of a Pi the choice of the OS to use is of paramount importance. It's going to define everything we'll be able to do on our Pi so you want to get this right. There are 2 key things were are looking for in our OS.

- 64-bit
- Headless
  
[64-bit](https://en.wikipedia.org/wiki/64-bit_computing) means that we will be able to use all of the memory available to us on our 8gb Pi 4. A 32-bit system can only address 4gb of memory. Now you might be thinking "well I'm using a 4gb board so I'll just use a 32-bit OS". That would be a bad idea. In the near future Minecraft will be [dropping support for 32 bit systems](https://www.minecraft.net/en-us/article/minecraft-1-18-2-pre-release-1). When? Who knows. But support for 32 bit java will soon be gone so it's best to get used to it now. Besides, you should, in theory, be getting better performance on a 64-bit arch. Also this guide is based on a 64-bit OS so some if it may not work at 32-bit.

A [headless](https://en.wikipedia.org/wiki/Headless_computer) OS simply means that there is no graphical user interface. A GUI uses a lot of system resources and simply put there are not a lot of resources available. We need all possible system resources available to run the server. This means that you'll be connecting to your Pi over a network connection. We'll explain that later.

So with those 2 criteria in mind that limits our choices. Fortunately those limited choices are good ones. The recommended OS for your Pi server is [Ubuntu Server](https://ubuntu.com/download/raspberry-pi). We are currently recommending version [21.10](https://ubuntu.com/download/raspberry-pi/thank-you?version=21.10&architecture=server-arm64+raspi) but only until the end of April 2022 when the new 22.04 LTS version comes out. Ubuntu has a large community of users and there is a ton of online documentation. It's tried and tested and is the OS that is supported for PiCubed. 

Now you might be asking "what about [Raspbian](https://www.raspberrypi.com/software/operating-systems/#raspberry-pi-os-64-bit)". The [64-bit lite](https://downloads.raspberrypi.org/raspios_lite_arm64/images/raspios_lite_arm64-2022-01-28/2022-01-28-raspios-bullseye-arm64-lite.zip) version of the official Pi OS has only recently been released. Time will tell if it will become the favorite over Ubuntu for Raspberry Pi servers but for now Ubuntu is still the recommended OS. You should also know that there are small differences in the Pi OS that make the installation process slightly different than what's explained here. We'll point them out where we can but be warned that if you don't use the supported OS, you're on your own.


---

# How cool are you?

Well if you are here reading this I'd say you're pretty cool but that's not going to help your server if it's a hot potato. To get the most out of your Pi 4 we're going to be overclocking the CPU. Having a server running constantly on an overclocked Pi will produce heat. Heat is the enemy of your system. Temperatures of over 80°c will cause your Pi to throttle and you will see undesirable effects on the performance of your server. To keep this heat in check you will need a cpu fan for your Pi. The most [basic](https://www.raspberrypi.com/products/raspberry-pi-4-case-fan/) of fans will do. If you don't like basic you might like something a little more [beefy](https://www.jeffgeerling.com/blog/2019/raspberry-pi-4-might-not-need-fan-anymore). I run Ice towers on all of my Pi servers.


---

# SD or SSD?

Without question the biggest performance upgrade you can make to your server is the addition of an external SSD (Solid State Drive). The Pi comes with an integrated SD (Secure Digital) card slot. For many Pi applications this is sufficient. For a Minecraft server SD fails on at least 2 points.

- Read & Write speeds
- Reliability
  
At present the only way to connect an SSD to a Pi 4 is through a USB connection. This USB connection will limit the maximum speed of your SSD transfer rates but this will still be many times faster than the fastest SD cards. Minecraft will be reading and writing to your storage device at least every 5 minutes to autosave the world. If your storage isn't fast enough you will experience lag during these save events.

SD cards are also not the most reliable storage medium, especially the cheap ones that are typically sold with a Pi. The constant reading a writing reduces their life span. Losing your Minecraft world due to a corrupt SD card is not something you want to experience.

Now SSD's do have a few cons. The is the extra cost. You will need the SSD and a way to connect it to your Pi. An SSD is also an extra power draw on your Pi. Sometimes needing more power than your Pi can supply. There's also a few extra steps to getting your Pi configured with an SSD. On the latest Pi 4's though this is not as much of an issue as in the past. Even with these issues however the performace gains far outweigh any cons.

If you really don't want to invest in a full SSD at the very least get the fastest USB key you can find and use that as your storage device. Make sure to use one that has USB 3.0 or higher. You won't get as much of a performance boost but it's an ok middle ground to


---

# Do you have the power?

One rarely mentioned and even more often overlooked component of your Pi Minecraft server is the power supply. Simply put you cannot get more out of your Pi than what you are putting into it. If the Pi is struggling the get the power it needs to operate it is designed to throttle itself to lower speeds in order to avoid damage. Don't kid yourself into thinking that the old phone charger you have sitting around will be enough to power your Pi. It will not. At the bare minimum use an official Raspberry Pi power supply. They reliably supply 3A of power to your Pi and are a good starting point. I say at the bare minimun though because we'll be adding fans, overclocking the Pi and hopefully external storage. All of these things will be drawing extra power and it's not a bad idea to upgrade your power supply a little. There are [3.5A power supplies](https://www.canakit.com/raspberry-pi-4-power-supply.html) for basically the same price as a 3A official power supply. I've used these on a few of my servers with no issues. Lately though I've been testing out 4A power supplies to see if there are any performance benifets. So far the jury is out on that question.