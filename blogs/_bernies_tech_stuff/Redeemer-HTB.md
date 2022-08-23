---
layout: post
title: Redeemer-HTB
date: 14/08/2022
tags: 
---
# Redeemer-HTB

## Attacking Ip info
Ip: **10.129.74.155**

### Task 1
Q:  *What does the 3-letter acronym FTP stand for?*
A: File Transfer Protocol. 

Doing a typical nmap scan  wont result in seeing what port is open. Note the box note mentions *redis* which a quick google search will show that redis server runs on tcp port 6379.

We can also try using nmaps --top-ports flag to see if we can pick it up that way.
```shell
PORT     STATE SERVICE VERSION
6379/tcp open  redis   Redis key-value store 5.0.7

```
### Task 2
Q:  *Which service is running on the port that is open on the machine?* 
A: redis

Redis is a in memory data structure store that supports abstract data structures.

### Task 3
Q:  *What type of database is Redis? Choose from the following options: (i) In-memory Database, (ii) Traditional Database*
A: In-memory Databse

### Task 4
Q:  *Which command-line utility is used to interact with the Redis server? Enter the program name you would enter into the terminal without any arguments.*
A: redis-cli

### Task 5
Q:  *Which flag is used with the Redis command-line utility to specify the hostname?*
A: -h
`
### Task 6
Q:  *Once connected to a Redis server, which command is used to obtain the information and statistics about the Redis server?*
A: info
- note: ip address is different because i needed to reset the machine
- I found out whqat command to use through looking and the redis manual.
- the HELP command provides a list of commands that i could use to view different commands avaialable to me. h]
 ``help @server``
```SHELL
redis-cli -h 10.129.60.214
10.129.60.214:6379> INFO
# Server
redis_version:5.0.7
redis_git_sha1:00000000
redis_git_dirty:0
redis_build_id:66bd629f924ac924
redis_mode:standalone
os:Linux 5.4.0-77-generic x86_64
arch_bits:64
multiplexing_api:epoll
atomicvar_api:atomic-builtin
gcc_version:9.3.0
process_id:755

```
### Task 7
Q:   *What is the version of the Redis server being used on the target machine?*
A:  5.0.7

### Task 8
Q:  *Which command is used to select the desired database in Redis?*
A: select
``help @generic``

### Task 9
Q:   *How many keys are present inside the database with index 0?*
A: 4

### Task 10
Q:  *Which command is used to obtain all the keys in a database?*
A: keys *
```shell
10.129.60.214:6379> keys *
1) "numb"
2) "temp"
3) "stor"
4) "flag"
10.129.60.214:6379> 

```

# GET THAT FLAG

Note that listing all the keys lists all the name of the different keys of the redis server. And lucky for us, the fourth one is conviently named flag!

using the command ``DUMP flag`` will retrieve the contents and give us the key needed