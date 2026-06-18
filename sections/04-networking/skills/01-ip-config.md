# Skill: Configuring IP Addressing

---

## Accessing Network Connections

- Run `Win + R` → type `ncpa.cpl`

This opens **Network Connections**, showing all network adapters on the device — typically **Ethernet** and **Wi-Fi**, along with any virtual adapters (e.g. VPN or virtual switches).

---

## Viewing and Editing IPv4 Settings

1. Right-click the relevant adapter (e.g. **Ethernet**) → **Properties**
2. Select **Internet Protocol Version 4 (TCP/IPv4)** from the list
3. Click **Properties**

This opens the IPv4 configuration window, showing:

| Field | Description |
|-------|-------------|
| **IP address** | The device's current address on the network |
| **Subnet mask** | Defines the size of the local network — e.g. `255.255.255.0` |
| **Default gateway** | The router address used to reach networks outside the local subnet |
| **Preferred / Alternate DNS server** | DNS servers used to resolve hostnames |

By default this is usually set to **Obtain an IP address automatically** (DHCP). Selecting **Use the following IP address** allows manual configuration.

---

## Changing the IP Address

- Select **Use the following IP address**
- Enter a new address, ensuring it falls within the valid range for the subnet and is not already in use by another device
- Subnet mask and gateway typically remain consistent with the rest of the network — only the host portion of the address usually needs to change
- Click **OK** to apply

> **Note:** Assigning an IP address outside the valid range for the subnet, or one already in use by another device (causing an IP conflict), will result in loss of connectivity. Always confirm the valid range and check for conflicts before assigning manually.

---

## Confirming the Change

Open a terminal and run:

```cmd
ipconfig /all
```

This confirms the IP address, subnet mask, gateway, and DNS servers currently assigned to the adapter, reflecting the change just made.

---

## Related Ticket

No dedicated ticket for this skill — IP configuration via the GUI is covered as part of the underlying skill set demonstrated in [TKT-005: User has no internet access on a newly built machine](../../02-cli-and-gui-tools/tickets/TKT-005.md), which uses the PowerShell equivalent of this process.