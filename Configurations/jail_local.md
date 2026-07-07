# jail.local configuration 

_path = /etc/fail2ban/jail.local_
  
```xml
enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
backend = %(sshd_backend)s
maxretry = 5
findtime = 60
bantime = 3600
```
---

<img width="1920" height="1103" alt="Screenshot from 2026-06-02 17-55-49" src="https://github.com/user-attachments/assets/72185ffd-60d3-488c-946e-2e2d1d9bfd8c" />
