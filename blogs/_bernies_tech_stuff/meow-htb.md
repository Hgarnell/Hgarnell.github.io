---
layout: post
title: 
date: 13/08/2022
last_updated: 13/08/2022
tags: 
---
# Meow - HTB

### Initial Setup
First i needed to vpn into the Hackthe box servers using openvpn, and the configuration files from HTB. I used the ```-b``` tack to run openvpn in the background. This will remain the same for all boxes in starting point
```shell
sudo -b openvpn  starting_point_kumarimo.ovpn
```

## Target details
Target Machine IP Address: **10.129.5.163**

#### Task 1
Q: *What does the acronym VM stand for*
A: Virtual Machine

#### Task 2
Q: *What does the acronym VM stand for*
A: Virtual Machine

#### Task 3
Q: *What tool do we use to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection? It's also known as a console or shell.*
A: Terminal

#### Task 3
Q: *What tool do we use to interact with the operating system in order to issue commands via the command line, such as the one to start our VPN connection? It's also known as a console or shell.*
A: Terminal

#### Task 4
Q:  *What is the abbreviated name for a 'tunnel interface' in the output of your VPN boot-up sequence output?*
A: Tun

#### Task 5
Q: *What tool do we use to test  ur connection to the target with an ICMP echo request?*
A: ping

#### Task 6
Q: *What is the name of the most common tool for finding open ports on a target?* 
A: nmap

#### Task 7
Q: *What service do we identify on port 23/tcp during our scans?*
A: tELNET

#### Task 8
Q: *What username is able to log into the target over telnet with a blank password?*
A: root

## The flag!
After telnetting into the attack Ip address  was greated with a prompt to provide a username, from the prior task i can assume it is root. Once logged in used ls to view the contents of the directory I was in. There I see there is a txt file called flag.txt. 

I used cat to read the file which provided the flag needed to  complete the  box.

