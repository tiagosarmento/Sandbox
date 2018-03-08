# Sandbox RaspberryPi

# Table of Contents
&nbsp;&nbsp;[1. Software License Agreement](#1-software-license-agreement)
<a name="1. Software License Agreement"/>  
&nbsp;&nbsp;[2. RaspberryPi Project](#2-raspberrypi-project)
<a name="2. RaspberryPi Project"/>  
&nbsp;&nbsp;[3. RaspberryPi OS](#3-raspberrypi-os)
<a name="3. RaspberryPi OS"/>  
&nbsp;&nbsp;&nbsp;&nbsp;[3.1. OS Install](#31-os-install)
<a name="3.1. OS Install"/>  
&nbsp;&nbsp;&nbsp;&nbsp;[3.2. OS Setup](#32-os-setup)
<a name="3.2. OS Setup"/>  

# 1. Software License Agreement
**MIT License**

**Copyright (c) 2018 Tiago Sarmento Santos**

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

# 2. RaspberryPi Project
This RaspberryPi Sandbox project aims to held a toolbox with several utilities for this platform.

# 3. RaspberryPi OS

## 3.1. OS Install
The OS in use under this project is the **RASPBIAN STRETCH WITH DESKTOP**, further instructions on how to prepared SD Card and OS installation can be found here: [raspbian-stretch](https://www.raspberrypi.org/downloads/raspbian/ "Raspbian for Raspberry Pi") 

## 3.2. OS Setup
Depending on the usage you will give to your RaspberryPi you may want to follow some of the following setup procedures.
If you are runnig an headless RaspberryPi, you may be interested by the SSH, Wi-Fi and VNC setup below.

### 3.2.1. Enable SSH
When running an headless RaspberryPi, you may want to enable the SSH to be able to access RaspberryPi remotely.
This can be done by adding a file named **ssh**, without any extension, onto the **boot** partition of the SD Card from another computer, complete details can be found here: [enable-ssh-raspberrypi](https://www.raspberrypi.org/documentation/remote-access/ssh/README.md "Enable SSH for remote access to Raspberry Pi")

### 3.2.2. Enable Wi-Fi
When running an headless RaspberryPi, you may want to enable the Wi-Fi to be able to access RaspberryPi remotely.
This can be done by adding a file named **wpa_supplicat.conf**, onto the **boot** partition of the SD Card from another computer.
The file contents should be as this example for a WPA2-PSK wireless network:
```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
network={
    ssid="WIFI_SSID"
    psk="WIFI_PASSWD"
    key_mgmt=WPA2-PSK
}
```
Further details on Wi-Fi setup, can be found here: [enable-wifi-raspberrypi](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md "Enable Wi-Fi for remote access to Raspberry Pi")

### 3.3.3. Enable VNC
When running an headless RaspberryPi, you may want to enable the VNC to be able to access RaspberryPi GUI (x-server) remotely.
Details on VNC setup, can be found here: [enable-vnc-raspberrypi](https://www.realvnc.com/en/connect/docs/raspberry-pi.html "Enable VNC for remote access to Raspberry Pi")

### 3.2.3. Reduce used space by OS
Depending on the usage you will give to your RaspberryPi you may want to reduce the used space by removing unused applications.
Hereafter a list of applications not used so often, by removing them space used by OS dropped to about 2.5GB.
```
wolfram-engine
libreoffice
scratch
minecraft-pi
sonic-pi 
dillo
gpicview
bluej
scratch2
greenfoot
python3-thonny
idle-python
netsurf
epiphany
node
htop
claws-mail
```
These can be removed as following: 
```
$ sudo apt-get remove --purge <APPLICATION_NAME>
$ sudo apt-get clean
$ sudo apt-get autoremove
```
There is also some "python_games", this can be removed as following:
```
$ sudo rm -rf /home/pi/python_games
```
