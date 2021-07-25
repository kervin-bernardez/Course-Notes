## Information Gathering

Passive : gathering information without establishing contact between the pen tester and the target

Active : gathering information involving contact between the pen tester and the actual target

### Hunter.io (email)

[hunter.io link](https://hunter.io/)

### Gathering Breached Credentials

google/darkweb

### theHarvester (email, name, subdomain, ip url)

[theHarvester Github](https://github.com/laramies/theHarvester)

```
theharvester -d tesla.com -l 500 -b google
```

### subdomain

[Sublist3r Github](https://github.com/aboul3la/Sublist3r)

```
sublist3r -d tesla.com
```

<!--certificate searching-->
[crt.sh link](https://crt.sh/) 

[OWASP Amass Github](https://github.com/OWASP/Amass)

```
amass intel -d tesla.com -whois

amass enum -passive -d tesla.com -src

amass enum -active -d tesla.com -brute -w path_to_wordlist.txt -src 
```

### website technologies

[builtwith](https://builtwith.com/)

[Wappalyzer link](https://www.wappalyzer.com/)

### Burpsuite

[burpsuite link](https://portswigger.net/burp/communitydownload)

browse normally with burp as proxy and intercept off

### Google Fu

[google dorking](https://ahrefs.com/blog/google-advanced-search-operators/)

```
site:tesla.com
filetype:pdf
```

### Soc Med

linkedin.com -> Images

linkedin.com -> People

### Hunting Breached Credentials

[paid credential hunting](https://dehashed.com) 

--- 

Check if subdomain is alive 

[httprobe Github](https://github.com/tomnomnom/httprobe)
