# Web App Enumeration

### assetfinder (subdomains)

[Assetfinder Github link](https://github.com/tomnomnom/assetfinder)

```
go get -u https://github.com/tomnomnom/assetfinder
```

```
assetfinder tesla.com
assetfinder --subs-only tesla.com
```

### amass (subdomains)

[amass Github link](https://github.com/OWASP/Amass)

```
go get -v github.com/OWASP/Amass/v3/...
cd $GOPATH/src/github.com/OWASP/Amass
go install ./...
```

```
amass enum -d tesla.com
```

### httprobe (alive subdomains)

[httpprove Github link](https://github.com/tomnomnom/httprobe)

```
go get -u github.com/tomnomnom/httprobe
```

```
cat tesla.com/recon/final.txt | httprobe
```

### gowitness (screenshots)

[gowitness Github link](https://github.com/sensepost/gowitness)

```
go get -u gorm.io/gorm
go get -u https://github.com/sensepost/gowitness
```

```
gowitness single https://tesla.com
```

### automating the enumeration process

run.sh
```bash
#! /bin/bash

url=$1

if [ ! -d "$url" ]; then
    mkdir $url
fi

if [ ! -d "$url/recon" ]; then
    mkdir $url/recon
fi

if [ ! -d "$url/recon/gowitness" ]; then
    mkdir $url/recon/gowitness
fi

echo "[+] Harvesting subdomains with assetfinder..."
assetfinder $url >> $url/recon/assets.txt
cat $url/recon/assets.txt | grep $1 >> $url/recon/final.txt
rm $url/recon/assets.txt

echo "[+] Harvesting subdomains with Amass..."
amass enum -d $url >> $url/recon/f.txt
sort -u $url/recon/f.txt >> $url/recon/final.txt
rm $url/recon/f.txt

echo "[+] Probing for alive domains..."
cat $url/recon/final.txt | sort -u | httprobe -s -p https:443 | sed 's/https\?:\/\///' | tr -d ':443' >> $url/recon/alive.txt

echo "[+] Running gowitness against all complied domains..."
gowitness file -s $url/recon/alive.txt -d $url/recon/gowitness
```

[sumrecon Github link](https://github.com/thatonetester/sumrecon)

[TCM's modified script](https://pastebin.com/MhE6zXVt)

### Additional Resources

[The Bug Hunter's Methodology](https://www.youtube.com/watch?v=uKWu6yhnhbQ)

[Nahamsec Recon Playlist](https://www.youtube.com/watch?v=MIujSpuDtFY&list=PLKAaMVNxvLmAkqBkzFaOxqs3L66z2n8LA)
