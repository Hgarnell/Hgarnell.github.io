---
layout: post
title:Over the wire: Bandit 0 to 4
date: 25/09/2022
tags: blog
---
# Overthewire-BANDIT
*Contains spoilers! aka the password*
## Level 0 
SSH stands for secure shell and allows us to securely connect to another computer from our own computer over a network. We are told to connect to the host at **bandit.labs.overthewire.org** on port 2220 with the username and password of bandit0. To do this we can use the following command

``ssh bandit0@bandit.labs.overthewire.org -p 2220``
ssh indicates that we are using the ssh protocol
bandit0@ indicates we are trying to access the host computer with the user bandit0 
the flag -p inidicates what port, which is 2220

## Level 0 -> 1
After logging into the machine. we are told the password for the next level is found in a file named *readme*
we can list all of the files in the directory we are in using *ls*, and the file *readme* should show up
then we can read the file in several ways, i chose to use the *cat* command, which stands for concatanate and basically just reads out the contents of said file.
we can then use the password found in that file to login to the host with the user bandt1!

NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

## Level 1 -> 2
Same concept as the previous level, however the file that contains the password is `-` because of this we can't do cat `-` and will need to use a different method.
``cat ./-``

rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

## Level 2 -> 3

Same concept as the previous level, however the file that contains the password is `spaces in the filename` because of this we can't do cat spaces in the filename and will need to use a different method.
``cat  spaces\ in\ this\ filename`` or
``cat  "spaces in this filename"``

aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

## Level 3 -> 4

For this level, we need to view a hidden file in another directory.  to change our directory, we can use the `cd` command.
Once we are in that directory, and use the ls command, it seems there is nothing in it.
 to view all directories inside a directory we use the `ls` command. the ls command shows all contents of a directory except for those that begin with a dot we need to use the `-a` flag. when doing that, we can see that there is a file in the directory, and can cat out the flag we need for the next level.
 
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe