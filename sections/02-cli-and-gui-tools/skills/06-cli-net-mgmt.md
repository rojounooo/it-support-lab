# Skill: Network Management Using the Command Line

---

## Accessing the Command Prompt

- Open the **Start Menu** and search for **cmd**
- Or run `Win + R` → type `cmd`

---

## `ipconfig` — IP Configuration

Displays the network configuration for all adapters on the device.

```cmd
ipconfig                      # Shows IPv4, IPv6, subnet mask, and default gateway per adapter
ipconfig /all                 # Extended output — includes MAC address, DHCP server, DNS servers, and lease information
```

### Flags

```cmd
ipconfig /release             # Releases the current DHCP-assigned IP address
ipconfig /renew               # Requests a new IP address from the DHCP server
ipconfig /flushdns            # Clears the local DNS resolver cache
```

> **Note:** `ipconfig /release` will fail if the adapter is configured with a static IP address — there is no DHCP lease to release.

---

## `ping` — Test Connectivity

Sends ICMP echo requests to a target to test whether it is reachable and measure response time.

```cmd
ping google.com               # Tests connectivity to a hostname
ping 8.8.8.8                  # Tests connectivity to an IP address
ping -t google.com            # Continuous ping — runs until stopped with Ctrl + C
```

> **Note:** A failed ping does not always mean the host is unreachable — some devices and firewalls block ICMP requests by default.

---

## `netstat` — Network Statistics

Displays active connections, listening ports, and protocol statistics.

```cmd
netstat -a                    # Shows all active connections and listening ports
netstat -b                    # Shows the executable associated with each connection (requires admin)
netstat -n                    # Displays addresses and port numbers in numerical form rather than resolving hostnames
```

These can be combined:

```cmd
netstat -an                   # All connections in numerical format — faster output, no DNS lookups
```

---

## `nslookup` — DNS Lookup

Queries DNS to resolve a hostname to an IP address, or to check which DNS server is being used.

```cmd
nslookup google.com           # Resolves the hostname and shows which DNS server responded
nslookup 8.8.8.8              # Reverse lookup — resolves an IP address to a hostname
```

Useful for diagnosing DNS resolution failures — if `ping google.com` fails but `ping 8.8.8.8` succeeds, the issue is DNS rather than connectivity.

---

## `net share` — View Shared Resources

Lists all shared folders and resources on the local machine.

```cmd
net share
```

---

## `net use` — Map Network Drives

Connects to a shared network resource and optionally maps it to a drive letter.

```cmd
net use Z: \\SERVER\SharedFolder              # Maps a network share to drive Z:
net use Z: \\SERVER\SharedFolder /persistent:yes   # Reconnects automatically on login
net use Z: /delete                            # Disconnects the mapped drive
```

---

## `tracert` — Trace Route

Traces the path packets take from the local machine to a destination, showing each hop and its response time.

```cmd
tracert google.com
```

Useful for identifying where in the network a connection is failing or experiencing high latency.

---

## `pathping` — Combined Ping and Trace Route

Combines the functionality of `ping` and `tracert`. Sends packets to each hop over a period of time and calculates packet loss and latency at every point along the route.

```cmd
pathping google.com
```

> **Note:** `pathping` takes longer to complete than `tracert` as it collects statistics at each hop over multiple intervals. Use `tracert` for a quick route check and `pathping` when you need detailed packet loss data.

---

## Related Ticket

→ [TKT-010: User unable to reach internal resources — suspected DNS issue](../tickets/TKT-010.md)