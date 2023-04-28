---
layout: post
title: Preignition-HTB
date: 15/08/2022
last_updated: 15/08/2022
tags: blog
---
# Preignition-HTB

## Attacking Ip info
Ip: **10.129.212.80**


#### Task 1
Q: *What is considered to be one of the most essential skills to possess as a Penetration Tester?*
A: Dir busting

short for directory busting

#### Task 2
Q: *What switch do we use for nmap's scan to specify that we want to perform version detection*
A: -sV

#### Task 3
Q: *What does Nmap report is the service identified as running on port 80/tcp?*
A: http

```shell
nmap -sV 10.129.212.80                                   
Starting Nmap 7.91 ( https://nmap.org ) at 2022-08-15 00:47 EDT
Nmap scan report for 10.129.212.80
Host is up (0.27s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    nginx 1.14.2

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 55.50 seconds

```

#### Task 4
Q: *What server name and version of service is running on port 80/tcp?*
A: ngnix 1.14.2

- nginx is a web server that can also be used as a reverse proxy, load balancer, mail proxy and HTTP cache.
- 
#### Task 5
Q: *What switch do we use to specify to Gobuster we want to perform dir busting specifically?*
A: dir

I used the following command with gobuster
``$ gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -x ".html,.txt,.php"  -u 10.129.50.56 -t 25 --timeout 60s 
- note ip is different because i needed to reset the machine a few times
- I also included the -t and --timeout swithes.
	- -t indicated the amount of requests it can send at a time
	- --timeout indicated the amount of time before it times outs. I had an issue with dirbuster timing out before actually getting to any webpages
	- -x  indicates the extensions we are looking for``
#### Task 6
Q: *What page is found during our dir busting activities?*
A: admin.php

#### Task 7
Q: *What is the HTTP status code reported by Gobuster for the discovered page?*
A: 200
```shell
$ gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -x ".html,.txt,.php"  -u 10.129.50.56 -t 25 --timeout 60s 
```

# GET THAT FLAG
TO get to the flag we can navigate to the admin.php page. There we are prompted with a login page where we can *guess* the username and password to get the flag!
