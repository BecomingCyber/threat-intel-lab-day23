# 🔐 SSH Hardening Tips – Defending Against Brute Force Attacks

Brute force attacks on SSH are a common threat. Here are simple ways to secure your server:

---

## 1️⃣ Disable Root Login

**Why:** Root is the first target during brute force attacks.

```bash
sudo nano /etc/ssh/sshd_config
Set:
PermitRootLogin no

Then restart SSH:
sudo systemctl restart ssh
```

## 2️⃣ Use SSH Key Authentication Only

**Why:** Stronger than password authentication.

```bash
sudo nano /etc/ssh/sshd_config
```
Set:
```bash
PasswordAuthentication no
```
Upload your public key to ~/.ssh/authorized_keys, then restart SSH.

## 3️⃣ Change Default SSH Port

**Why:** Avoid mass scans that look for port 22.

Edit:
```bash
sudo nano /etc/ssh/sshd_config
```
Change:
```bash
Port 2222
```
Restart:
```bash
sudo systemctl restart ssh
```

## 4️⃣ Use fail2ban to Auto-Ban Offenders
Why: Blocks IPs after repeated failed logins.

Install and enable:
```bash
sudo apt install fail2ban -y
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```

Basic jail configuration:
```bash
sudo nano /etc/fail2ban/jail.local
```
Example:
```bash
[sshd]
enabled = true
port = ssh
filter = sshd
logpath = /var/log/auth.log
maxretry = 5
bantime = 3600
```
Restart:
```bash
sudo systemctl restart fail2ban
```

## 5️⃣ Set Up a Firewall (e.g., UFW)
```bash
sudo ufw allow 2222/tcp   # if you changed SSH port
sudo ufw enable
```
## 6️⃣ Monitor Login Activity Regularly
Command:

```bash
sudo grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr
```
Or install log monitoring tools like:

- Logwatch

- GoAccess

- Elastic Stack (ELK)

