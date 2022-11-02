---
layout: post
title:Over the wire: Bandit 4 to 10
date: 26/09/2022
tags: 
---
# Overthewire-BANDIT
*Contains spoilers! aka the password*

## Level 10 -> 11
We are told that the  password is stored in the `data.txt` file but is encoded in base64
	base64 is a binary to text encoding method and is used to represent binary data
	- wikipedia
 Base64 can often be identified with a string of characters ending with `==` . In this case when we open the file as is, we get the following.
```shell
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIDZ6UGV6aUxkUjJSS05kTllGTmI2blZDS3pwaGxYSEJNCg==
```

to decode it we canse use the base64 command along with the flag --decode to get the following output.

```shell
bandit10@bandit:~$ cat data.txt | base64 --decode
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```

## Level 11 -> 12
Reading the data.txt file by itself makes it seem like the data is encoded with some sort of rotation algorithim like a caeser cipher. After reading the directions for this level I see that it is a rot13 shift meaning that each letter is rotated to the 13th letter, meaning A becomes N, B becomes O etc. 
```shell
bandit11@bandit:~$ cat data.txt
Gur cnffjbeq vf WIAOOSFzMjXXBC0KoSKBbJ8puQm5lIEi
```
To solve this, we can use the `tr` command which is short for transliterate.  we can pipe the output from data.txt into the command `tr 'A-Za-z' 'N-ZA-Mn-za-m'`
and get the following output!
```shell
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```


## Level 12 -> 13
We are told that the data.txt file is a hexdump, which can be seen from reading the file as is
```
00000070: 000d 0069 91ea 0c6d 5100 0068 00c8 000d  ...i...mQ..h....                                                     00000080: 0323 4340 3d40 0d0d 1a68 01a3 4c83 401a  .#C@=@...h..L.@.                                                     00000090: 687a 4034 0340 1a00 3468 0188 c868 34d0  hz@4.@..4h...h4.                                                     000000a0: 00c8 d01a 6874 d323 40d3 d206 81a1 a680  ....ht.#@.......                                                     000000b0: d0c8 0190 d034 0340 0d00 c800 01a6 991a  .....4.@........                                                     000000c0: 0019 3400 d000 0006 800c 4d1a 0189 a001  ..4.......M.....                                                     000000d0: fc18 2890 6086 162a 8035 6a6b 3d5c 1382  ..(.`..*.5jk=\..                                                     000000e0: 0a38 e6dd 214b 6fa4 3984 0192 256e e084  .8..!Ko.9...%n..                                                     000000f0: ed6b ad67 3318 b07a 005d 0e21 dbd1 fb84  .k.g3..z.].!.... 
```
Overthewire recconmends we create a new directory inside of the tmp directory to store our work,.
to do this i used the following command
``mkdir /tmp/testclaol``
and copied over the data.txt file using the `cp` command

To reverse hexdump we can use `xxd -r` to reverse the hexdump and then put the output into a new file. and reading out the output will give us the following.
```shell
bandit12@bandit:~$ xxd -r /tmp/testclaol/data.txt > /tmp/testclaol/data1.txt
bandit12@bandit:~$ cat /tmp/testclaol/data1.txt
4M(`*5jk=\#@4@]~9?Ͽ>; P44
8!Ko9%nkg3z]!w_D00y(S0qY@u<[J4C۞sV==kGLs$W1 cE.cLA
2|ꂠNu6,rHz0,YSZ!Nj3a BdqB;n^~s.P       D{g<@Hi`pɬPʭ"ouU~     \;$H$qJHHd{O;;$H@oZTxC!V<a+nfpg)HZ0ːErE8P]e"?
```
We can check out what type of file we have now using the `file` command and we see that is a .bin file with gzip compressed data. To be able to unzip it using the `gunzip` command, we bneed to add the gz prefix.  This level is annoying because there is alot of unzipping. I wont go into all of the detail, but through using the file command and adding the required suffix, i used the `gunzip`,`bunzip2`, and `tar -xvf`, commands along with copying and moving files after i've unzipped them to make things clearer , i was able to get the password!

wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw
## Level 13 -> 14
To get the password for bandit level 14, we need to use the sshkey given to us to ssh into the bandit14 user account. Similar to how we ssh into bandit normally from our local host we can use the following command
``ssh -i sshkey.private bandit14@localhost -p 2220`` 

fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

## Level 14 -> 15

For this level the password for level15 casn be found by sending the password for this level to the next on port 3000 on the localhost.

At first I was kind of confused on how to approach this. Using SSH like thee perivous level failed. SSH is an encrypted connection hence the name secure shell, but netcat just connects that lets you write and read easily so in this case hte netcat command is rthe best option.

to connect to the localhost on port 3000 i just used the following command
```shell
bandit14@bandit:~$ nc localhost 30000
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
```

## Level 15 -> 16
For this level we are told to use ssl. SSL uses  handshake authentication process and signs data to provide integrity.

To use ssl when uising netcat we can use the --ssl option
```shell
bandit15@bandit:~$ ncat --ssl localhost 30001
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```

## Level 16 -> 17

For this level  we are given the hint that it can be found  by submitting the password of the current level to a port on the local host within the range of 31000 and 32000 that speaks ssl.

We can do this easily with nmap! by using the -p 31000 and 32000 to specify the port range and the ssl cipher
--script ssl-enum-ciphers

we get the following output which hints to us that the correct port may be
```shell
bandit16@bandit:~$ nmap  localhost -p 31000-32000 -T4 -sC -sV --script ssl-enum-ciphers
.....
......
31960/tcp open  echo
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port31790-TCP:V=7.80%T=SSL%I=7%D=11/2%Time=63622555%P=x86_64-pc-linux-g
SF:nu%r(GenericLines,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20cu
SF:rrent\x20password\n")%r(GetRequest,31,"Wrong!\x20Please\x20enter\x20the
SF:\x20correct\x20current\x20password\n")%r(HTTPOptions,31,"Wrong!\x20Plea
SF:se\x20enter\x20the\x20correct\x20current\x20password\n")%r(RTSPRequest,
SF:31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\
SF:n")%r(Help,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x
SF:20password\n")%r(SSLSessionReq,31,"Wrong!\x20Please\x20enter\x20the\x20
SF:correct\x20current\x20password\n")%r(TerminalServerCookie,31,"Wrong!\x2
SF:0Please\x20enter\x20the\x20correct\x20current\x20password\n")%r(TLSSess
SF:ionReq,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20pa
SF:ssword\n")%r(Kerberos,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x
SF:20current\x20password\n")%r(FourOhFourRequest,31,"Wrong!\x20Please\x20e
SF:nter\x20the\x20correct\x20current\x20password\n")%r(LPDString,31,"Wrong
SF:!\x20Please\x20enter\x20the\x20correct\x20current\x20password\n")%r(LDA
SF:PSearchReq,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x
SF:20password\n")%r(SIPOptions,31,"Wrong!\x20Please\x20enter\x20the\x20cor
SF:rect\x20current\x20password\n");
```

port 31790!
Using the command fromthe last level we can submit the current password to port 31790 to recieve the next using ncat with the specific --ssl tack.
```shell
bandit16@bandit:~$ ncat --ssl localhost 31790
JQttfApK4SeyHwDlI9SXGR50qclOAil1
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```
Interestingly its an RSA public key!