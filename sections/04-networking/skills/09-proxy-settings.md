# Skill: Configuring Proxy Settings

---

## What is a Proxy?

A proxy server acts as an intermediary between a client device and the internet. Rather than connecting directly to a website, the device sends its request to the proxy, which forwards it on behalf of the device and returns the response. 

Proxies are commonly used in organisations to:

- Filter and control web access (e.g. blocking certain categories of sites)
- Log and monitor outbound web traffic
- Cache frequently accessed content to reduce bandwidth
- Enforce security policies by routing traffic through an inspection point

---

## Configuring Proxy Settings

1. Open **Settings → Network & Internet → Proxy**
2. Under **Manual proxy setup**, toggle **Use a proxy server** to **On**
3. Enter the proxy server address and port number provided by the network administrator
4. Optionally add addresses to the **exceptions list** — these will bypass the proxy (e.g. internal company addresses that should be accessed directly)
5. Click **Save**

> **Note:** In managed environments, proxy settings are typically pushed automatically via Group Policy or Intune rather than configured manually on each device. Manual configuration is most relevant for standalone machines, troubleshooting, or testing.

---

## Automatic Proxy Configuration

Some organisations use a **PAC (Proxy Auto-Configuration)** file instead of a manually entered address. This is a script hosted on the network that tells the device which proxy to use depending on the destination:

1. Under **Automatic proxy setup**, toggle **Use setup script** to **On**
2. Enter the URL of the PAC file provided by the network administrator

---

## Testing the Proxy Configuration

Once configured, test that traffic is routing through the proxy correctly:

1. Open a browser and navigate to a site that would normally be accessible — confirm it loads
2. If the proxy enforces filtering, attempt to navigate to a blocked category — confirm access is denied and a block page is returned
3. To verify the proxy address the browser is actually using, visit a site such as `whatismyip.com` — the IP shown should reflect the proxy server's address rather than the device's local IP

> **Note:** If the proxy is misconfigured or unreachable, the device will lose internet access entirely since all traffic is directed through it. If connectivity drops after configuring a proxy, double-check the address, port, and whether the proxy server is reachable on the network.

---

## Related Ticket

→ [TKT-021: User unable to access external websites — proxy configuration required](../tickets/TKT-021.md)
