---
layout: post
title:Over the wire: Bandit 17 to 24
date: 26/09/2022
tags: blog
---
# Overthewire-BANDIT
*Contains spoilers! aka the password*

## Level 17-> 18

to login into this level we need to use the rsa key that we recieved in the previous level. 
using the -i flag we can indicate that we are not using a password to login like we've done in previous levels. I stored the rsa key in a new file under my bandit directory on my local computer using the nano command.

Your ssh command may look something like this
``ssh bandit17@bandit.labs.overthewire.org -i id_rsa -p 2220``

We are then told that there are two files on the attack machine, one called `passwords.old` and `passwords.new`. The password is the line that is different in passwords.new. To find the difference we can use the ``diff`` command which makes life alot easier!

```shell
bandit17@bandit:~$ ls
passwords.new  passwords.old
bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< 09wUIyMU4YhOzl1Lzxoz0voIBzZ2TUAf
---
> hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg

```

## Level 18 -> 19
When trying to login to the next level we are automatically logged out because someone has eddited the .bashrc script.
To  ssh without it we can just use dash rather than bash hich is a simplistic shell compared to bash.
To do this we can just tag on /bin/dash at the end of our ssh script
``ssh bandit18@bandit.labs.overthewire.org -p 2220 /bin/dash``
Since we are using a dash shell rather than bash it will look different compared to other levels.
 To get the password we just need to read the cat file  which will result in
 ``awhqfNnAbc1naukrpqDYcF95h7HoMTrC``

## Level 19 -> 20
For this level we are told to use the setuid binary in the home directory.

What is the setuid binary?
Its a binary file that we can execute in the homedirectory called `bandit20-do`
To learn how to use it we can execute the file.
```shell
bandit19@bandit:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id

```
running the binary file with the command ./bandit20-do id runs the id command as if we were the user bandit20.

We know the password for this level can be found in its usual place which is under the file `/etc/bandit_pass/bandit20`

```shell
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
VxCazJaVykI6W36BkBU0mJTCM8rR95XT

```

## Level 20 -> 21
