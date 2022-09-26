---
layout: post
title: Appointment-htb
date: 15/08/2022
last_updated: 15/08/2022
tags: 
---
# Appointment

# Attack machine info
IP address: **10.129.125.69

### Task 1
Q: *What does the acronym SQL stand for?*
A: Structured Query Language

### Task 2
Q: *What is one of the most common type of SQL vulnerabilities?*
A: SQL Injection

### Task 3
Q: *What does Pii stand for>?*
A: Personalyl Identifiable Information

### Task 4
Q: *What does the OWASP Top 10 list name the classification for this vulnerability*
A: Ao3:2021-Injection

### Task 5
Q: *What service and version are running on port 80 of the target?*
A:  Apache httpd 2.4.38 ((Debian))
``└─$ nmap -sV -sC 10.129.25.69 -Pn``
Need to use the flag -Pn because the IP was blocking nmaps ping probs.
```shell
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
|_http-title: Login

```
### Task 6
Q: *What is the standard port used for the HTTPS protocol?*
A: 443
### Task 7
Q: *What is one luck-based method of exploiting login pages?*
A: brute-forcing

### Task 8
Q:  *What is a folder called in web-application terminology?*
A: directory

### Task9
Q:  *What response code is given for "Not Found" errors?*
A: 404

### Task 10
Q: *What switch do we use with Gobuster to specify we're looking to discover directories, and not subdomains?*
A: dir

### Task 11
Q: *What symbol do we use to comment out parts of the code?*
A: #

# GET THAT FLAG
i tried to brute force the username and password combo with generic parameters such as admin:admin password:password etc however none of them worked.

Note how the box has talked about SQL injectionn which could be a hint. I know that we can trick the box parameters into thinking the statement is done by adding a ``'#`` to the first username to comment out the password to get and sql statement that liikes like
```SQL
	SELECT user WHERE username = 'admin' #' && password = 
```
Note how the password and the one  ``'`` is commented out? This lets us login because there is no santization of input.