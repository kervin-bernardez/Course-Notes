## Scanning & Enumeration

### nmap

```
nmap -T4 -p- -A 10.10.10.10 -v

nmap -T4 -p -sU 10.10.10.10 -v

nmap -sC -sV 10.10.10.10 
```

### nikto

```
nikto -h http://10.10.10.10
```

### gobuster 

```
gobuster dir -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -u http://10.10.10.10
```

### smbclient

```
smbclient -L \\10.10.10.10

smbclient -L \\10.10.10.10\ADMIN$
```

### SSH

<!--bannerGrabbing-->
```
telnet 10.10.10.10 22

nc -v 10.10.10.10. 22
```

### exploit searching

thru google search (i.e. https://www.exploit-db.com/, https://www.rapid7.com/db/, ...)

```
serchsploit samba 2.2

serchsploit -m path/to/exploit
```

---

### Masscan

```
mascan -p1-65535 10.10.10.10
```

### Metasploit

auxiliary/scanner/... 

### Nessus

New Scan -> Basic Network Scan -> Name -> Targets -> DISCOVERY -> Scan Type (Port scan (all ports)) ->  ASSESSMENT -> Scan Type (Scan for known web vulnerabilities) -> SAVE

New Scan -> Advanced Scan -> Name -> Targets -> DISCOVERY -> 
