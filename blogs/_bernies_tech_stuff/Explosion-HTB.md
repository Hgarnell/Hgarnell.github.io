---
layout: post
title: Explosion-HTB
date: 15/08/2022
last_updated: 15/08/2022
tags: 
---
# Explosion-HTB

# Attack machine info
IP address: **10.129.1.13**

### Task 1
Q: *What does the 3-letter acronym RDP stand for?*
A: Remote Desktop Protocol
	-RDP is a secure network communication protocol created by microsoft to use a desktop computer.. remotely... kinda self explanitory. 

### Task 2
Q: *What is a 3-letter acronym that refers to interaction with the host through a command line interface?*
A: cli ( Command Line interface)

### Task 3
Q: *What about graphical user interface interactions?*
A: gui

### Task 4
Q: *What is the name of an old remote access tool that came without encryption by default and listens on TCP port 23?*
A: TELNET

### Task 5
Q: *What is the name of the service running on port 3389 TCP?*
A: ms-wbt-server 
```shell
PORT     STATE SERVICE       VERSION
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp  open  microsoft-ds?
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: EXPLOSION
|   NetBIOS_Domain_Name: EXPLOSION
|   NetBIOS_Computer_Name: EXPLOSION
|   DNS_Domain_Name: Explosion
|   DNS_Computer_Name: Explosion
|   Product_Version: 10.0.17763
|_  System_Time: 2022-08-14T01:05:03+00:00
| ssl-cert: Subject: commonName=Explosion
| Not valid before: 2022-08-13T00:45:24
|_Not valid after:  2023-02-12T00:45:24
|_ssl-date: 2022-08-14T01:05:12+00:00; 0s from scanner time.
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

```
### Task 6
Q: *What is the switch used to specify the target host's IP address when using xfreerdp?*
A: /v:
found using ``xfreerdp -h``
- Free rdo us a free rdp protocol library released under apache

## GET THAT FLAGG

uSING the username Administrator without a password will let