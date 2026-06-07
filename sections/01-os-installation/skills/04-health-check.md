# Skill: Running a PC Health Check and Updating Drivers

---

## Requirements

| Item | Details |
|------|---------|
| Windows 11 Client | Device to be audited |
| Internet Connection | Required for downloading driver updates |

---

## Steps

### 1. Open Windows Security

- Open the **Start Menu** and search for **Windows Security**
- Select **Device Performance & Health** from the left sidebar

---

### 2. Review the Health Report

The health report audits four areas and flags any issues found:

| Area | What It Checks |
|------|---------------|
| **Storage Capacity** | Available disk space — flags if the drive is running low |
| **Battery Life** | Battery health and whether it is affecting performance (laptops only) |
| **Apps & Software** | Identifies apps with known compatibility issues or that failed to update correctly |
| **Windows Time Service** | Confirms the system clock is syncing correctly — time drift can cause authentication failures and other issues |

Each area will show a green tick if no issues are found, or a warning if action is required. Select any flagged item for more detail on the recommended action.

> **Note:** A clean report is worth documenting. Screenshots of all green are useful evidence that the device is in a healthy state before it is issued or returned to a user.

---

### 3. Run Windows Update

Before checking drivers, ensure Windows itself is up to date — some driver issues are resolved through Windows Update directly.

- Open **Settings → Windows Update**
- Select **Check for Updates** and install any pending updates
- Restart if prompted before continuing

---

### 4. Check for Driver Updates via Device Manager

Driver issues may not surface in the health report. Check Device Manager for any flagged devices:

- Right-click the **Start** button and select **Device Manager**, or run `devmgmt.msc`
- Look for any devices marked with a **yellow warning triangle** — these indicate a missing or problematic driver
- Right-click the flagged device and select **Update Driver → Search automatically for drivers**
- Allow Windows to search and install any available update

> **Note:** If Windows cannot find an updated driver automatically, visit the manufacturer's website (e.g. Intel, NVIDIA, Realtek) and download the driver directly. This is common for display adapters and network cards.

---

### 5. Verify

- Restart the device if any updates or driver changes were applied
- Reopen Device Manager and confirm no warning triangles remain
- Reopen the Windows Security health report and confirm all areas are clear

---

## Related Ticket

→ [TKT-004: User reports device running slowly and behaving erratically — health check requested](../tickets/TKT-004.md)