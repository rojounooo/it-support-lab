# Skill: Update Drivers via Device Manager

---

## Requirements

| Item | Details |
|------|---------|
| Windows 11 Client | Device with outdated or missing drivers |
| Internet Connection | Required for automatic driver search |

---

## Steps

### 1. Open Device Manager

- Right-click the **Start** button and select **Device Manager**, or run `devmgmt.msc` from the Run dialog (`Win + R`)

---

### 2. Identify Problematic Drivers

- Scan the device list for any entries marked with a **yellow warning triangle** — these indicate a missing, outdated, or malfunctioning driver
- Expand categories if needed to locate flagged devices

> **Note:** A device may function partially without the correct driver but cause performance issues or unexpected behaviour. Not all driver problems surface as warning triangles.

---

### 3. Update the Driver

- Right-click the flagged device and select **Update Driver**
- Select **Search automatically for drivers**
- Windows will search locally and via Windows Update for a compatible driver and install it if found

---

### 4. Manual Driver Install (Fallback)

If Windows cannot find a driver automatically:

- Note the device name from Device Manager
- Visit the manufacturer's website (e.g. Intel, NVIDIA, Realtek, AMD) and search for the device by name or model
- Download the appropriate driver for Windows 11 and run the installer

> **Note:** This is common for display adapters and network cards, particularly on fresh installs where generic drivers are loaded by default.

---

### 5. Verify

- Restart the device if prompted
- Reopen Device Manager and confirm the warning triangle is gone
- The device should now appear under its correct category without any flags

---

## Related Ticket

→ [TKT-004: User reports device running slowly and behaving erratically — health check and driver audit requested](../tickets/TKT-004.md)