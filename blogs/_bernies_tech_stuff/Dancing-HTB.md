---
layout: post
title: Dancing-HTB
date: 14/08/2022
last_updated: 14/08/2022
tags: 
---
# Dancing-HTB

# Attack machine info
IP address: **10.129.1.12**

### Task 1
Q: *What does the 3-letter acronym SMB stand for?*
A: Server Message Block
	- What is SMB? acommunication protocol that provides shared access to files and printers across a network. 

### Task 2
Q: *What port does SMB use to operate at?*
A: 445

Using Nmap to view what ports are open we can see that there are three ports open on the attack ip.
```shell
PORT    STATE SERVICE                                                        
135/tcp open  msrpc                                                          
139/tcp open  netbios-ssn                                                    
445/tcp open  microsoft-ds   
```
- Msrpc stands for microsoft remotre procedure call, and allows client server software communication.
- Netbios-ssn  is NetBIOS sessions service and is a protocol that connects two computers transmitting heavy data traffic
- Microsoft DS is the name given to port 445 which is used by **SMB**, aha

### Task 3
Q: *What is the service name for port 445 that came up in our nmap scan*
A: microsoft-ds

### Task 4
Q: *What is the 'flag' or 'switch' we can use with the SMB tool to 'list' the contents of the share?*
A: -L
We can use the tool smbclient with the aformentiond -L flag to list all the contents of the share.

### Task 5
Q: *What is the name of the share we are able to access in the end with a blank password?*
A: WorkShares
We can use the tool smbclient with the aformentiond -L flag to list all the contents of the share.

### Task 6
Q:  *What is the command we can use within the SMB shell to download the files we find?*
A: get
 Note to download the files we need to get into the actual smb server first. We can do that through using smbclient.
 I used
 ```shell
 smbclient //10.129.1.12/WorkShares
```
I would get an error first  saying there werent enough \ in the service whithout using the / before the ip, even though it was fine with using the L switch.
Once logged in i can browse the server and i see there are two shares, one for amy and one for james.
Using ls to view all the content, i see james's share contains the flag.txt that im looking for

## The Flag!
I used get to download the flag to my local directory!




