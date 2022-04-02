---
layout: default
title: Configure your Raspberry Pi
nav_order: 3
description: How to configure your Raspberry Pi
---
sudo apt update

sudo apt upgrade -y

sudo reboot

sudo nano /boot/firmware/config.txt

#Disable the Wifi and Bluetooth  
dtoverlay=disable-wifi  
dtoverlay=disable-bluetooth

#Set the SD card slot to poll only once  
dtparam=sd_poll_once

#Set the GPU memory to minimum  
gpu_mem=16

#Overclock your Pi  
over_voltage=6  
arm_freq=2147

cntrl+x  
y  
enter  

sudo reboot

To view the time on your server use the command 'date'.  
Typically, your server will generate an output with the default UTC time zone.  
UTC is Coordinated Universal Time, the time at zero degrees longitude.  
To change your time zone you can use the 'timedatectl' command.  
First, run this command to generate a list of available time zones:  
'timedatectl list-timezones'  
A list of time zones will print to your screen. You can press SPACE to page down, and b to page up. Once you find the correct time zone, make note of it then type q to exit the list.  
Next, you can set the time zone with timedatectl set-timezone by replacing the highlighted portion with the time zone you found in the list. You’ll need to use sudo with timedatectl to make this change:  
'sudo timedatectl set-timezone America/New_York'  
You can verify your changes by running 'date' again.  
