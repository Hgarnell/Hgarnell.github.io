---
layout: post
title: Fawn-HTB
date: 16/09/2022
last_updated: 16/09/2022
tags: #HTB
---
# HTB Fawn

# Attack machine info
IP address: **10.129.239.17**

### Task 1
Q:  *What does the 3-letter acronym FTP stand for?*
A: File Transfer Protocol. 

### Task 2
Q:  *Which port does the FTP service listen on usually?*
A: 21

### Task 3
Q:  *What acronym is used for the secure version of FTP?*
A: SFTP

### Task 4
Q:  *What is the command we can use to send an ICMP echo request to test our connection to the target?*
A: pin g

### Task 5
Q:  *From your scans, what version is FTP running on the target?*
A: 21
```SHELL
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
Service Info: OS: Unix

```
### Task 6
Q:  *From your scans, what OS type is running on the target?*
A: unix

### Task 7
Q:  *What is the command we need to run in order to display the 'ftp' client help menu?*
A:  ftp -h
```shell
ftp -h

        Usage: { ftp | pftp } [-46pinegvtd] [hostname]
           -4: use IPv4 addresses only
           -6: use IPv6, nothing else
           -p: enable passive mode (default for pftp)
           -i: turn off prompting during mget
           -n: inhibit auto-login
           -e: disable readline support, if present
           -g: disable filename globbing
           -v: verbose mode
           -t: enable packet tracing [nonfunctional]
           -d: enable debugging

```

### Task 8
Q:  *What is username that is used over FTP when you want to log in without having an account?*
A: anonymous

## GET THAT FLAG
running with the script tag on nmap will show us that there is a flag.txt file being kept on the ftp server and that anonymous logging is allowed
```shell
nmap -sV -sC 10.129.239.17                                         130 ⨯
Starting Nmap 7.91 ( https://nmap.org ) at 2022-08-13 03:36 EDT
Nmap scan report for 10.129.239.17
Host is up (0.27s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_-rw-r--r--    1 0        0              32 Jun 04  2021 flag.txt
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
|      At session startup, client count was 4
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
Service Info: OS: Unix

```
Using that to our advantage we can get the flag by using ftp and the username anonymous to pull down the flag.txt file to get the flag.

