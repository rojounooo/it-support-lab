# Skill: Configure Internet Access via PowerShell

---

## Requirements

| Item | Details |
|------|---------|
| Windows 11 Client | Device with no network configuration |
| Ethernet Connection | Physical cable connected to the device |
| Network Details | IP address, subnet mask, default gateway, and DNS server to assign |

---

## Steps

### 1. Open PowerShell as Administrator

- Right-click the **Start** button and select **Windows Terminal (Admin)** or **PowerShell (Admin)**

---

### 2. Identify the Network Adapter

Before assigning an IP, confirm the exact alias of the Ethernet adapter:

```powershell
Get-NetAdapter
```

Look for the adapter with **MediaType** of `802.3` (Ethernet) and note its **Name** — typically `Ethernet` or `Ethernet 2`.

---

### 3. Assign a Static IP Address

Use `New-NetIPAddress` to assign the IP configuration to the adapter:

```powershell
New-NetIPAddress -InterfaceAlias "Ethernet" -IPAddress "192.168.1.50" -PrefixLength 24 -DefaultGateway "192.168.1.1"
```

| Parameter | Description |
|-----------|-------------|
| `-InterfaceAlias` | The adapter name identified in Step 2 |
| `-IPAddress` | The static IP address to assign |
| `-PrefixLength` | Subnet mask in CIDR notation — `24` equals `255.255.255.0` |
| `-DefaultGateway` | The router or gateway address for the network |

---

### 4. Assign a DNS Server

`New-NetIPAddress` does not set DNS — this is done separately:

```powershell
Set-DnsClientServerAddress -InterfaceAlias "Ethernet" -ServerAddresses "8.8.8.8"
```

> **Note:** `8.8.8.8` is Google's public DNS server and is suitable for lab use. In a corporate environment this would point to an internal DNS server, typically the domain controller.

---

### 5. Verify Connectivity

Confirm the configuration was applied correctly:

```powershell
Get-NetIPAddress -InterfaceAlias "Ethernet"
```

Then test connectivity:

```powershell
Test-Connection google.com
```

A successful reply confirms the IP, gateway, and DNS are all configured correctly.

---

## Related Ticket

→ [TKT-005: User has no internet access on a newly built machine](../tickets/TKT-005.md)