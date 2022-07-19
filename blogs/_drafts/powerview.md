**powerview**

> Powerview is a powershell tool to gain network situational awareness on Windows domains. It contains a set of powershell replacements for various windows net* commands utilising PowerShell AD hooks and win32 api functions for useful windows domain functionality. also includes metafunctions and some custom written user functions to identify where specific users are logged into

Powershell  is used for enumerating a windows domain AFTER you have already gained a shell into the system

```bash
# start Powershell
powershell -ep bypass # -ep bypasses the exec policy of powershell letting you run scripts easily


#starting powerview
. .\Downloads\PowerView.ps1

#Enumerating a list of the Domain users
Get-Net-User | select cn
```

![](/Users/bgarnell/Library/Application%20Support/marktext/images/2022-01-25-10-47-52-image.png)

```bash
# Enumerate through the domain groups that include admin


get-netgroup -groupname *admin*
```

Other Interesting  commands

Invoke-sharefinder - finds nonstandard shared on hosts in the local domain

Get-netcomputer -fulldata |select operatingsystem - for finding the operatin system on the domains
