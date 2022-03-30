---
layout: default
title: Configure your Raspberry Pi
nav_order: 3
description: How to configure your Raspberry Pi
---
sudo nano /boot/firmware/config.txt

Disable the Wifi and Bluetooth
dtoverlay=disable-wifi
dtoverlay=disable-bluetooth

Set the SD card slot to poll only once
dtparam=sd_poll_once

Set the GPU memory to minimum
gpu_mem=16

Overclock your Pi
over_voltage=6
arm_freq=2100
