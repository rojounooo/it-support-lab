# Skill: Install Windows 11 from Install Media

> **Note:** This guide assumes a clean install without a product key.

---

## Requirements

| Item | Details |
|------|---------|
| PC / Laptop | Reliable internet connection required |
| USB Flash Drive | 8GB minimum — will be wiped during the process |
| Product Key | Optional |

---

## Steps

### 1. Download the Media Creation Tool

Download **MediaCreationTool.exe** from the official Microsoft page:

[Windows 11 Download — microsoft.com](https://www.microsoft.com/en-gb/software-download/windows11)

---

### 2. Create Bootable Media

- Insert the USB drive and ensure it is empty, or back up any files on it as it will be wiped
- Run the Media Creation Tool and select the USB drive as the target media

---

### 3. Boot from USB

- Insert the USB into the target device and power it on
- The device should boot into the Windows Installation Wizard automatically

> **Note:** If the wizard does not load, enter BIOS and change the boot device priority to the USB drive.

---

### 4. Installation Settings

Work through the wizard using the following settings:

| Setting | Value |
|---------|-------|
| Language to install | Region-specific, e.g. English (United Kingdom) |
| Time and currency format | Region-specific, e.g. English (United Kingdom) |
| Keyboard | Region-specific or preferred layout |
| Setup option | Install Windows 11 |
| Product key | Enter key or select **I don't have a product key** to skip |
| Select image | Windows 11 Pro |
| Licence terms | Accept to continue |
| Installation location | Disk 0 Unallocated Space |

> **Note — Keyboard:** For ISO layout keyboards, US input is sometimes preferred.

> **Note — Edition:** The available editions are context-dependent. Education is common in schools; Enterprise is typical in large organisations.

> **Note — Disk selection:** If the device has multiple disks installed, all will appear here. Select the correct one.

---

### 5. Local User Creation

- Confirm Country/Region and Keyboard layout when prompted
- At the Microsoft account sign-in screen, select **Join a domain** to skip the Microsoft account requirement and proceed with a local account

---

## Related Ticket

→ [TKT-001: New device requires Windows 11 installed before being issued to a user](../tickets/TKT-001.md)