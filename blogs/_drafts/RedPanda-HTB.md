---
layout: post
title:Red Panda 
date: 11/09/2022
tags: blog
---
# Red Panda-HTB

## Attacking Ip info
Ip: **10.10.11.170**

### Recon
#### Nmap Scan
```shell
└─$ nmap 10.10.11.170 -Pn                                                                                                                                                                                                                1 ⨯
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2022-09-11 03:05 EDT
Stats: 0:01:38 elapsed; 0 hosts completed (1 up), 1 undergoing Connect Scan
Connect Scan Timing: About 99.99% done; ETC: 03:07 (0:00:00 remaining)
Nmap scan report for 10.10.11.170
Host is up (0.20s latency).
Not shown: 904 closed ports, 94 filtered ports
PORT     STATE SERVICE
22/tcp   open  ssh
8080/tcp open  http-proxy


```

Ports 22 and 8080 are open. Which indicates to us that secure shell is open, and that the machine is potentially running a webite.

### Port 8080: 