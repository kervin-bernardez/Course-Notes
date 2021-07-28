## OWASP Top 10

[OWASP Testing Checklist](https://github.com/tanprathan/OWASP-Testing-Checklist)

[OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/assets/archive/OWASP_Testing_Guide_v4.pdf)

### SQL Injection 

In-band SQLi
```
' OR 1=1; --;
```

Blind SQLi
```
(sleep 5)
```

Defenses:
- Parameterized Statements
- - ie. SELECT * FROM users WHERE email =?
- Sanitizing Inputs

### Broken Authentication 

```
permits automated attacks
permits weak passwords
weak forgot-password process
exposed sessionid
```

example
```
X invalid username
X invalid password

✓ invalid username or password
```

### Sensitive Data Exposure

```
discovering item that is exposed

check for security headers
check for ssl cipher stength
```

directory fuzzing
```
ffuf -w /usr/share/dirb/wordlists/small.txt -u http://10.10.10.10/FUZZ

backups                [Status: 301, ...
```

ssl enumeration 
```
nmap --script=ssl-enum-ciphers -p 443 tesla.com
```

[securityheaders.com](https://securityheaders.com/)

### XML Enternal Entities (XXE)

Classic XXE
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
<stockCheck><productId>&xxe;</productId></stockCheck>
```

[XXE Payloads Github link 1](https://github.com/payloadbox/xxe-injection-payload-list)

[XXE Payloads Github link 2](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XXE%20Injection/README.md)

### Broken Access Control

```
user get access to somewhere they should'nt

example 
- normal user can access /admin
- insecure direct object references (IDOR)
```

### Security Misconfiguration

```
missing approriate security hardening

example 
- default credentials
- unnecessary ports/accounts
- stack trace
```

### Cross Site Scripting

Reflected XSS (client side)
```
<script>alert(1)</script>
```

Stored XSS (server side)
```
<script>alert(1)</script>
```

[Stored XSS Payloads Github link](https://github.com/payloadbox/xss-payload-list)

DOM XSS (client side)

[DOM Based XSS Blog](https://www.scip.ch/en/?labs.20171214)

Defenses:
- Encoding
- - `< becomes &lt;`
- - `<script> becomes &lt;script>`
- Filtering
- - `<script> becomes script`
- Validating
- - compare inpute against white list
- Sanitization
- - combination of escaping, filtering, and validation

### Insecure Deserialization

```
user serialize malicous payload -> server deserialize and execute code

example 
- php serialize() unserialize()
```

### Using Components with Known Vulnerability

```
known vulnerabilities

example
- Apache Tomcat < 9.0.1 (Beta) / < 8.5.23 / < 8.0.47 / < 7.0.8 - JSP Upload Bypass / Remote Code Execution
```

### Insufficient Logging and Monitoring

