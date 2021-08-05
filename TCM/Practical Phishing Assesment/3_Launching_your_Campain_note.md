### Testing your Infrastructure

```
sudo ./gophish
```

Login to Gophish

1. Sending Profiles -> New Profile
2. Name: Testing
3. From: (email to be spoofed)
4. Username: (Smtp Username)
5. Password: (Smtp Password)
6. Host: (Smpt ServerName:Port)
7. Send Test Email -> Send
8. Save Profile

### Creating Gophish Campaign

1. Users & Groups -> New Group
2. Name: (LIVE)
3. Bulk Import Users
4. Save changes
5. Email Templates -> New Template
6. Name: (LIVE TEMPLATE)
7. Subject: URGENT: Suspicious login from moscow
8. HTML: (message)
9. ✓ Add Tracking Image
10. Save Template
11. Landing Pages -> New Page
12. Name: (live)
13. Save Page
14. Sending Profiles -> New Profile
15. Name: (LIVE)
16. From: (email to be spoofed)
17. Host: (Smpt ServerName:Port)
18. Username: (Smtp Username)
19. Password: (Smtp Password)
20. Save Profile

### Sending Your Phishing Campaign

1. Campaigns -> New Campaign
2. Name: (LIVE)
3. Email Template: (LIVE TEMPLATE)
4. Landing page: (live)
5. URL: ip
6. Groups: LIVE
7. Launch Campaign
8. Ok
