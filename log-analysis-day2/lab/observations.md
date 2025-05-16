# 🧠 Day 2 Observations - Log Analysis Basics: Windows Security Logs
# 🔍 What Did I Observe?
- Failed Login (Event ID 4625):
I simulated a failed login attempt by using an invalid password for the haxuser1 account.
The Security Log captured this attempt under Event ID 4625.
Details included:

- Username: haxuser1

- Failure Reason: Bad username or password

- Logon Type: 3 (network logon)

Successful Login (Event ID 4624):
After logging into the system successfully, Event Viewer recorded a successful login event under Event ID 4624.
Details included:

Logon Type: 2 (interactive login)

Authentication Package: NTLM

Account Lockout (Event ID 4740):
After multiple failed login attempts with the wrong password, the haxuser1 account was locked.
Event Viewer recorded this event under Event ID 4740.
Details included:

Locked Account: haxuser1

Caller Computer Name: My machine’s hostname

# 🧠 What Did I Learn?
Windows Security Logs are a powerful tool to detect unauthorized access attempts and track user activity.

Failed login attempts can be identified quickly by filtering for Event ID 4625.

Successful logins provide important details like logon type and authentication method.

Account lockouts can signal possible brute-force attacks or password guessing attempts, especially if they happen frequently.

Filtering specific Event IDs saves time and helps SOC Analysts find critical security events faster.

Real-world SOC teams monitor these Event IDs actively to detect intrusions and potential insider threats.

# 🛡️ Importance for a SOC Analyst:
SOC Analysts must constantly monitor Windows Security Logs for suspicious patterns such as:

Multiple failed logins from different accounts or IP addresses

Unexpected account lockouts

Privilege escalations after successful logins

Early detection of these events can help prevent security breaches and respond to threats before damage occurs.

