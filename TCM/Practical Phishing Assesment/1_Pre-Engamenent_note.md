### Researching Your Target

/ Look for names in targets websites

/ try to register a domain with similar name (AWS Route53)

i.e. 

youtube.com x unavailabe

youtubẹ.com ✓ available

phisihing.com x unavailabe

phisih1ng.com ✓ available

[altcodeunicode Website](https://altcodeunicode.com/)

### Gophish

[gophish Website](https://getgophish.com/)

Dashboards = admin panel

Campaigns = statistics on data

Users & Groups = who you sending your emails

Email Templates = what your email look like + tracking when email is opened

Landing Pages = what page you see when you click the link in the email

Sending Profiles = who the email is coming from

### Evilginx2

[evilginx2 Github link](https://github.com/kgretzky/evilginx2)

[evilginx2 Blog](https://breakdev.org/evilginx-2-next-generation-of-phishing-2fa-tokens/)

### AWS

purchase a Route53 domain

EC2 instance for hosting gophish and evilginx2 

S3 bucket for receiving emails

SES for verifying domain

### Creating Target Email List

/ Goto company page

/ Look for employee names

/ Look for email schema 

i.e.

first.last@domain.com

[](https://phonebook.cz)

[](https://www.linkedin.com/)

[CrossLinked Github link](https://github.com/m8r0wn/CrossLinked)

crosslinked
```
python3 crosslinked.py -f '{first}.{last}@domain.com' company_name
```

sort alphabetical w/o duplicates
```
cat names.txt | sort | uniq -u > namesFinal.txt
```

### Bypassing Spam Filters

- Keep it simple

- Don't copy Microsoft's emails

- Don't shoot yourself in the foot

- - Overtesting

- - Whitelisting

Timing your phish

- This is subjective and highly dependent on work environment

- Know your client's timezone

i.e.

7:00 PM @ before dinner (the last thing they wanna do is investigate they just wanna get this off as soon as possible to enjoy there time off)

### Introduction to tmux

```
tmux                            #start tmux session
ctrl+b d                        #detach from tmux session
tmux ls                         #list tmux sessions
tmux attach                     #attach to last session
tmux attach -t mysession        #attach to a session with the name mysession
```
