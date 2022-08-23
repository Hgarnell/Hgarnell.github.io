---
layout: post
title:Crocodile 
date: 16/08/2022
tags: 
---
# Crocodile-HTB

## Attacking Ip info
Ip: **10.129.253.137*

### Task 1
Q:  *What nmap scanning switch employs the use of default scripts during a scan?*
A: -sC

### Task 2
Q:  *What service version is found to be running on port 21?*
A:  vsFTPd 3.0.3 
```shell
Not shown: 998 closed ports
PORT   STATE SERVICE
21/tcp open  ftp
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| -rw-r--r--    1 ftp      ftp            33 Jun 08  2021 allowed.userlist
|_-rw-r--r--    1 ftp      ftp            62 Apr 20  2021 allowed.userlist.passwd
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.10.14.29
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
80/tcp open  http
|_http-title: Smash - Bootstrap Business Template

Nmap done: 1 IP address (1 host up) scanned in 56.70 seconds                                                                  
```
### Task 3
Q:   *What FTP code is returned to us for the "Anonymous FTP login allowed" message?*
A: 230

### Task 4
Q:  *What command can we use to download the files we find on the FTP server?*
A: get

### Task 5
Q:  *What version of Apache HTTP Server is running on the target host?*
A: admin

### Task 6
Q:  *What version of Apache HTTP Server is running on the target host?*
A:  2.4.41 

### Task 7
Q:  *What is the name of a handy web site analysis plug-in we can install in our browser?*
A: WAPPALYZER

### Task 8
Q:  *What switch can we use with gobuster to specify we are looking for specific filetypes?*
A: -x

### Task 9
Q:   *What file have we found that can provide us a foothold on the target?*
A: login.php