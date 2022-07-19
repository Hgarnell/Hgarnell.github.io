**Intro to Ffuf and how to use it**

- '*ffuf*' stands for 'fuzz faster you fool!'
  
  - Its a web attack tool written in go and is like the burpsuite of the cli
  
  - to use it you need the input file you're sending to the webapp and the location to be injected which is indicated with *FUZZ*
  
  - 

---

**FINDING PAGES OR FILES IN THE ROOT OF A SITE**

``ffuff -c -w /put/the/path/to/list/here -u http://domainnamegoeshere/FUZZ``

    -u specifies the url and -w specifies the wordlist. Both -u and -w are the minimum options that we need to supply to ffuf.

-c is not imgant and just helps colourize the output making the results easier to see.

    - make sure you have seclists installed. 

           -    path to seclists in kali in /usr/share/seclists/

    - you can use any keyword besides FUXX by defining it at the end of a wordlist.txt

`ffuf -u http://weburl/FUZZ -w usr/share/seclists/Discovery/Web-Content/big.txt`  or  ``usr/share/seclists/Discovery/Web-Content/web-extensions.txt

---

**web extension enumeration**

To enumerate through a giant file isnt always the best solution. Usually we can assume that index.<file extension name e.g txt/html> is the default page so we can from there determine the type of programming language used.

`` ffuf -u htttp://weburlgoeshere/indexFUZZ -w usr/share/seclists/Discovery/Web-Content/web-extentions.txt ``

****

**Filtering out extensions**

Ones we know the types of extensions supported by the webpage we can filter out the rest from a generic word lists using -e

``-e .php,.txt``

---

**Filtering out http status codes and other thingies**

By using <mark>-fc 403</mark> we can filter out all the output for the 403 http status code

by using <mark>-mc</mark> instead of fc we are asking it to match the specified code rather than filtering it out

to  filter out the size of different responses we can use <mark>-fs</mark>

![](/Users/bgarnell/Library/Application%20Support/marktext/images/2021-12-08-15-09-07-image.png)

if we want to match all files we can use a regexo beginning with a dotf

``ffuf -u http://10.10.196.129/FUZZ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-files-lowercase.txt -fr '/\..*'``

---

**Fuzzing parameters**

When we have the page or api endpoint and need to know the parameters that are accepted we can use fuxx

Finding a vuln parameter could lead us to xss,sql, path disclosure and command injection

T<mark>o generate a wordlist and save a fi</mark>le containing integers, we can use -w -w which tells ffuf to read a wordlist from stdout

    -       stdout stands  for standard output stream

this helps us in that lets us generate a list of integers with our command and pipe the output to fuff

```
$ ruby -e 'puts(0..255).to_a'| ffuf -u 'http://10.10.255.32/sqli-labs/Less-1/?id=FUZZ' -c-w - -fw 33        
```

We could also use ffuf for word-list based brute force password attacks like we do with burpsuite

``ffuff -u http://10.10.255.32/sqli-labs-Less-1/ -c -w /usr/share/seclists/Passwords/Leaked-Databased/hak5.txt -X POST -d 'uname=Dummy&passwd=FUZZ&SUBMIT=SUMBIT' -fs 1435 -H 'Content-Type:application/x-www-form-urlencoded'``

---

**Finding vhosts and subdomains**

Fuff might not be as good as other tools to find subdomain enumaertion but its still doable

``ffuff -u http://FUFFdomainhere.com -c -w /usr/share/seclists.Discover/DNS/subdomains-top1million-5000.txt``

Some subdomains might not be able to be found by the dns and can only be found by resolving the targets network to their dns server.

---

***proxing ffuf traffic***

You can send all the ffuf traffic through a web proxy using http or SOCKSS, its also possible to send only matches to your proxy to reply

``ffuff -u http://10.10.225.32/ -c -w /usr/share/seclists/Discover/Web-content common.txt -x http://127.0.0.1:8080``

`ffuff -u http://10.10.225.32/ -c -w /usr/share/seclists/Discover/Web-content common.txt -replay-proxy http://127.0.0.1:8080`

---

**other options**

- saving output to a markdown file
  
  - -of md -o fuff.md
    
    - -of specifices the the format while -o specifies the file


