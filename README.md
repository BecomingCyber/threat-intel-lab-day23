
# 🛡️ Day #23 – Threat Intelligence Basics

## 🎯 Objective
Investigate a phishing email by extracting Indicators of Compromise (IOCs) and using threat intelligence tools to evaluate their maliciousness.

---

## 📌 Extracted IOCs

| Type       | Value                                                                 |
|------------|------------------------------------------------------------------------|
| IP Address | `18.188.148.80`                                                       |
| Domain     | `aaronthompson.ug`                                                    |
| File Hash  | `d45a079c59c2860f9cf4578a8fc9f5fe8009cff8aaa83c572474d6bfe15ba95b`     |

---

## 🔍 IOC Analysis

### 🔹 IP Address: `18.188.148.80`

- **Tool:** [VirusTotal](https://www.virustotal.com/gui/ip-address/18.188.148.80)
- **Country:** 🇺🇸 United States
- **Autonomous System:** AS16509 (Amazon AWS)
- **Malicious Detection:** 1 / 94 security vendors flagged it as malicious

![IP Address Lookup](./images/IP_Address_Lookup.png)

---

### 🔹 Domain: `aaronthompson.ug`

- **Tool:** [urlscan.io](https://urlscan.io/result/...) + Abuse.ch ThreatFox
- **IP Location:** 🇷🇺 Russia (`217.8.117.45`)
- **AS Name:** CREXFEXPEX-RUSSIA
- **Malware Associations:** 
  - **Raccoon Stealer**
  - **AZORult**
- **Detected Technologies:** Debian OS, Apache Web Server

![Domain Lookup](./images/Domain_Lookup.png)

---

### 🔹 File Hash:  
`d45a079c59c2860f9cf4578a8fc9f5fe8009cff8aaa83c572474d6bfe15ba95b`

- **Tool:** [VirusTotal](https://www.virustotal.com/gui/file/d45a079c59...)
- **File Type:** `.7z` Archive
- **Filename:** `flv.exe-source-code.7z`
- **Size:** 1.14 MB
- **Detection Ratio:** 40 / 63 security vendors
- **Popular Labels:**
  - `Trojan:Win/BadJoke.QW`
  - `Trojan/Win32.Agent`
  - `MBR:Abobus-A`
- **Family Tags:** `badjoke`, `abobus`, `rjbli`

![File Hash Analysis](./images/File_Hash_Analysis.png)

---

## 🧠 Optional: Threat Intelligence Feed

- **Source:** [ThreatFox - Abuse.ch](https://threatfox.abuse.ch)
- **Domain:** `aaronthompson.ug`
- **IOC Tags:**
  - 5 malware samples
  - 2 malware families
  - Resolved to IP: `217.8.117.45`
  - Malware Names: `RaccoonStealer`, `AZORult`

![ThreatFox](./images/Optional_Bonus_Threat_Intelligence_Feeds.png)

---

## ✅ Summary Table

| IOC Type | Value                              | Threat Type/Family         | Tool Used      |
|----------|-------------------------------------|-----------------------------|----------------|
| IP       | 18.188.148.80                      | Possibly malicious (AWS)    | VirusTotal     |
| Domain   | aaronthompson.ug                   | RaccoonStealer, AZORult     | URLScan, ThreatFox |
| File Hash| d45a079c59...                      | Trojan, BadJoke, Abobus     | VirusTotal     |

---

## 📝 Conclusion

This phishing email was confirmed malicious based on:

- Known malware associations (Trojan, RaccoonStealer)
- Suspicious hosting in Russia
- Positive detection from multiple threat intelligence platforms

**🛑 Escalation Recommended:** Block domain, hash, and monitor for connections to 217.8.117.45.
