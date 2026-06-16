# Skill: Configuring Windows Defender Antivirus Settings

---

## Accessing Windows Security

- Open the **Start Menu** and search for **Windows Security**
- Select **Virus & threat protection** from the left sidebar

The main panel displays a summary of the most recent scan — date, duration, and number of threats found.

---

## Running a Scan

Click **Quick scan** to run an immediate scan, or select **Scan options** to choose the scan type.

### Scan Types

| Scan Type | Description |
|-----------|-------------|
| **Quick Scan** | Scans folders and file locations most commonly targeted by malware — the fastest option and suitable for routine checks |
| **Full Scan** | Scans every file and running program on the device — thorough but time-consuming |
| **Custom Scan** | Scans a specific folder or drive — useful when a threat is suspected in a particular location |
| **Microsoft Defender Offline Scan** | Restarts the device and runs a scan before Windows fully loads — used to detect and remove rootkits and persistent malware that active Windows processes may obscure |

---

## PowerShell — Check Defender Status and Run Scans

Windows Defender can also be managed via PowerShell, which is useful for remote management or scripting routine checks.

### Check Defender Status

```powershell
Get-MpComputerStatus
```

Returns the current state of Windows Defender including whether real-time protection is enabled, the last scan time, antivirus signature version, and whether any threats were detected.

Key fields to check:

| Field | Description |
|-------|-------------|
| `RealTimeProtectionEnabled` | Confirms real-time protection is active |
| `AntivirusSignatureLastUpdated` | Date of the last definition update |
| `QuickScanAge` | Days since the last quick scan |
| `FullScanAge` | Days since the last full scan |

---

### Run a Scan via PowerShell

```powershell
# Quick scan
Start-MpScan -ScanType QuickScan

# Full scan
Start-MpScan -ScanType FullScan

# Custom scan — specify the path to scan
Start-MpScan -ScanType CustomScan -ScanPath "C:\Users\Jane\Downloads"
```

---

### Update Definitions

```powershell
Update-MpSignature
```

Forces an immediate update of antivirus definitions rather than waiting for the scheduled update.

---

## Related Ticket

→ [TKT-012: User reports potential malware on device — antivirus scan and review required](../tickets/TKT-012.md)