# Skill: Restore Windows 11 After System File Corruption

> **Warning:** Deleting System32 files will render a machine unbootable. Only perform this on a VM or a device you are explicitly authorised to modify.

---

## Requirements

| Item | Details |
|------|---------|
| Windows 11 Client | A system where automatic repair has failed due to a corrupted or missing system file |
| Internet Connection | Required if using Cloud Download to source the reinstall files |

---

## Simulating the Fault

To reproduce the scenario in a lab environment, delete a critical System32 file to trigger boot failure:

- Open File Explorer and navigate to `C:\Windows\System32`
- Delete `ntoskrnl.exe` (the Windows kernel — its absence causes automatic repair to fail)
- Restart the machine

Windows will attempt automatic repair, fail, and present the recovery screen.

> **Note:** Take a VM snapshot before doing this so you have a clean restore point if needed.

---

## Steps

### 1. Reach the Recovery Screen

When automatic repair fails, Windows will display two options:

- **Shut Down**
- **Advanced Options**

Select **Advanced Options** to enter the Windows Recovery Environment (WinRE).

---

### 2. Navigate to Troubleshoot

From the **Choose an option** screen, select **Troubleshoot**.

This separates standard reset options from more advanced tools. From here you can access Startup Repair, System Restore, Command Prompt, and the reset options used in the next step.

---

### 3. Reset This PC

Select **Reset this PC**. Two options are presented:

| Option | Effect |
|--------|--------|
| Keep my files | Reinstalls Windows, preserves personal files in `C:\Users`, removes apps and settings |
| Remove everything | Full clean install — equivalent to a fresh Windows installation |

Select **Keep my files** — a corrupted OS does not require a full wipe. Personal data should be preserved where possible, and this is the least disruptive path to recovery.

> **Note:** Even with **Keep my files**, applications will need to be reinstalled after recovery. Advise the user of this before proceeding.

---

### 4. Choose a Reinstall Source

Two options are available:

| Option | Details |
|--------|---------|
| Cloud Download | Downloads a fresh copy of Windows from Microsoft's servers — requires a stable internet connection but ensures the latest version is used |
| Local Reinstall | Uses the existing Windows files on the device to rebuild — no internet required but may reintroduce corruption if the local files are compromised |

Select **Cloud Download** to ensure a clean, uncorrupted source.

---

### 5. Confirm and Reset

- Review the summary screen confirming the selected options
- Click **Reset** to begin
- The process will take some time and the device will restart multiple times — this is expected
- Once complete, Windows will boot to the initial setup screen

---

### 6. Post-Recovery

- Complete region, keyboard, and account setup
- Verify that personal files are intact under `C:\Users`
- Reinstall any applications that were removed during the reset
- Run Windows Update to ensure the system is fully patched

---

## Related Ticket

→ [TKT-002: User's PC fails to boot — automatic repair unsuccessful, manual recovery required](../tickets/TKT-002.md)