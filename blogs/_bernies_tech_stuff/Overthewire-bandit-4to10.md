---
layout: post
title:Over the wire: Bandit 4 to 10
date: 26/09/2022
tags: blog
---
# Overthewire-BANDIT
*Contains spoilers! aka the password*

## Level 4 -> 5
We are told the flag is hidden in a human readable file inside of the inhere directory.

to find the human readable file, we can use the file command to determine the file type and the `-i` flag which causes the output to describe the mime type strings.
We can specify that we want it to do said command on all files inside of the  directory but doing ``inhere/*`` with the asteriks specifying everything
```shell
file -i inhere/*
inhere/-file00: application/octet-stream; charset=binary
inhere/-file01: application/octet-stream; charset=binary
inhere/-file02: application/octet-stream; charset=binary
inhere/-file03: application/octet-stream; charset=binary
inhere/-file04: application/octet-stream; charset=binary
inhere/-file05: application/octet-stream; charset=binary
inhere/-file06: application/octet-stream; charset=binary
inhere/-file07: text/plain; charset=us-ascii
inhere/-file08: application/octet-stream; charset=binary
inhere/-file09: application/octet-stream; charset=binary
```
After executing that command we can see that the flag should be located in file 7

lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

## Level 5 -> 6
Same concept as the previous level, however we are given a bit more infromation on the file we need to find. the file is 1033 bytes and not executable. After reading the linux manual on how to use the find command, we can use the flags ``size`` to specify file size  followed by the number of bytes and `c` to specify we want bytes. then we use ``\! -executable`` to specify we want the file to not be executable. 
We then get only one file found with those attributes which is file2 in the maybeinhere07 directory.

```shell
 find /inhere -size 1033b \! executable
```
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

## Level 6-> 7

Same concept as the previous level  but there is no specific directory we need to search through.
the attributes of the file we are looking for are that it has 33 bytes, owned by the user bandit7 and bandit6 group. 
using the following command
``bandit6@bandit:/$ find *  -size 33c -user bandit7 -group bandit6``
we are given a lisdt of files, alot with permission denied erros, but the only one without it is the file we are looking for!

``var/lib/dpkg/info/bandit7.password``
catting that flag will give us the flag we need to proceed to the next level
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
## Level 7 -> 8

For this level we are told that the password is stored  next to the word millionth in the data.txt file.
If we try to read the data.txt file as is, it is wayyy to long.
To easily extract the line we can simply use the command
bandit7@bandit:~$ grep millionth data.txt

TESKZC0XvTetK0S9xNwm25STk5iWrBvP

## Level 8 -> 9

For this level the password is a unique line stored in the data.txt file.
to find that we can use the sort command and uniq command with the `-u` flag. We will also need to use the pipe operator to take the data from the sort command and pass it through uniq.

```shell
bandit8@bandit:~$ sort data.txt | uniq -u
```
EN632PlfYiZbn3PhVK3XOGSlNInNE00t

## Level 9 ->10
Same idea as the last few levels, we need to pull out a human readable text from a  binary file and are told that it is preceededby a few = symbols.

to do this we can use the strings command and pipe it through to grep and should get the following result!
```shell
bandit9@bandit:~$ strings data.txt | grep ===
========== the
bu========== password
4iu========== is
========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```