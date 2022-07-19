**Pokemon**

- Find the Grass-Type POkemon
  
  - First going to try and nmap into the attack machine and see what ports are open
  
  - ![](/Users/bgarnell/Library/Application%20Support/marktext/images/2021-12-09-15-27-55-image.png)

there are quite a few ports so it might be useful to look at the web server first.

- The webserver doesnt seem to have much but since port 22 is open we should be able to ssh into it.

- We can try and curl the webpage and see if there is anything interesting.
  
  <img src="file:///Users/bgarnell/Library/Application%20Support/marktext/images/2021-12-10-09-32-30-image.png" title="" alt="" data-align="center">- Password maybe?

- Using that user name and password to ssh into the attack machine, it works! and it looks like we are root

- ![](/Users/bgarnell/Library/Application%20Support/marktext/images/2021-12-10-09-36-48-image.png)

the Desktop and Videos directories look the most interesting.

Unzipping the zipped file in desktop gives us grass-type txt which should be our first flag.

![](/Users/bgarnell/Library/Application%20Support/marktext/images/2021-12-10-09-38-11-image.png)

```50 6f 4b 65 4d 6f 4e 7b 42 75 6c 62 61 73 61 75 72 ``` is whats in the file, which is hex for the flag PoKeMoN{Bulbasaur}
