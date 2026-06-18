# Skill: Configuring DNS Settings

---

## Accessing Network Connections

- Run `Win + R` → type `ncpa.cpl`

This opens **Network Connections**, showing all network adapters on the device — typically **Ethernet** and **Wi-Fi**.

---

## Viewing and Editing DNS Settings

1. Right-click the relevant adapter (e.g. **Ethernet**) → **Properties**
2. Select **Internet Protocol Version 4 (TCP/IPv4)** from the list
3. Click **Properties**

This opens the IPv4 configuration window, which shows the current DNS configuration alongside IP settings.

---

## Adding a Secondary DNS Server

- Under **Use the following DNS server addresses**, the **Preferred DNS server** field holds the primary DNS server
- The **Alternate DNS server** field can be used to add a secondary server, e.g. `8.8.8.8`
- Click **OK** to apply

> **Note:** The alternate DNS server is only used if the preferred server fails to respond — it acts as a fallback rather than being queried simultaneously. Adding a reliable secondary like `8.8.8.8` (Google) or `1.1.1.1` (Cloudflare) prevents a single DNS server outage from taking down name resolution entirely.

---

## Refreshing DNS After a Change

After changing DNS settings, clear and re-register the DNS cache to ensure the new configuration takes effect immediately rather than relying on cached entries:

```cmd
ipconfig /flushdns
```

Clears all cached DNS entries on the local machine, forcing future lookups to query the DNS server fresh rather than using a stale cached result.

```cmd
ipconfig /registerdns
```

Re-registers the device's DNS name with the DNS server — relevant in domain environments where the device's hostname needs to be resolvable by other machines on the network.

---

## Confirming the Change

```cmd
ipconfig /all
```

Confirms the preferred and alternate DNS servers currently assigned to the adapter, reflecting the change just made.

---

## Related Ticket

No dedicated ticket for this skill — DNS configuration via the GUI is the underlying setting exercised in [TKT-010: User unable to reach internal resources — suspected DNS issue](../../02-cli-and-gui-tools/tickets/TKT-010.md), which diagnoses and resolves a DNS issue via the command line.