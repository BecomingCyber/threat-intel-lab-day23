# 🛠️ Windows Setup - Day 2: Log Analysis Basics (Windows Security Logs)

---

## 🖥️ System Details

| Item | Description |
|:-----|:------------|
| OS | Windows 10 Pro (Version 22H2) |
| User Account | Local Admin Account |
| Tools Used | Event Viewer, PowerShell |

---

## 🛠️ Lab Environment Setup Steps

1. **Create Test User**
   - Open PowerShell (Admin) and create a test user:
     ```powershell
     New-LocalUser -Name "haxuser1" -NoPassword
     ```

2. **Set Account Lockout Policy (Optional)**
   - Open `secpol.msc`.
   - Navigate to:  
     `Account Policies ➔ Account Lockout Policy`
   - Configure:
     - Account lockout threshold: `3` invalid attempts
     - Account lockout duration: `1` minute
     - Reset account lockout counter after: `1` minute

3. **Simulate Events**
   - Failed Login Attempt (4625):
     ```powershell
     net use \\127.0.0.1\IPC$ /user:haxuser1 WrongPassword
     ```
   - Successful Login (4624):
     - Sign out and log back in with a valid user account.
   - Account Lockout (4740):
     - Repeat invalid login attempts 3+ times to trigger lockout.

4. **Enable Event Viewer Filtering**
   - Open `eventvwr.msc`.
   - Navigate to: `Windows Logs ➔ Security`.
   - Filter by Event IDs: `4624`, `4625`, and `4740`.

---

## 📦 Outputs Collected

- Screenshot of Event ID 4625 (Failed Login)
- Screenshot of Event ID 4624 (Successful Login)
- Screenshot of Event ID 4740 (Account Lockout)

---

✅ Environment Ready for Log Analysis
