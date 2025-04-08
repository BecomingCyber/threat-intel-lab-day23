# 🛠️ Windows Log Collection Setup

## Enable PowerShell Logging

1. Open `gpedit.msc`
2. Navigate to:
   - Computer Configuration → Administrative Templates → Windows Components → Windows PowerShell
3. Enable:
   - Module Logging
   - Script Block Logging
   - Script Execution Logging

## Simulate Suspicious PowerShell Activity

```powershell
Get-LocalUser | Select-Object Name, Enabled
Detect the Log
Open Event Viewer (eventvwr.msc)

Navigate: Applications and Services Logs > Microsoft > Windows > PowerShell > Operational

Filter by Event ID 4104

Find entry showing Get-LocalUser