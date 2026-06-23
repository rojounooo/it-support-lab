# Skill: Establishing a VPN Connection on Windows 11

A VPN (Virtual Private Network) creates an encrypted tunnel between a client device and a remote server, allowing secure access to resources on the remote network as if the device were physically connected to it. This is commonly used to give remote workers access to internal company resources.

---

## Requirements

| Item | Details |
|------|---------|
| Windows 11 Client | Device to connect from |
| VPN Server | A server configured to accept VPN connections — see note below |
| Server Address | The public IP or hostname of the VPN server |

> **Note:** For this lab, the VPN server is a Windows Server 2022 VM hosted in Azure with the Routing and Remote Access Service (RRAS) role enabled. This provides a real public endpoint rather than a local VM, and the setup is documented in the Section 9 Azure lab.

---

## Adding a VPN Connection

1. Open **Settings → Network & Internet → VPN**
2. Click **Add VPN**
3. Fill in the following fields:

| Field | Value |
|-------|-------|
| **VPN provider** | Windows (built-in) |
| **Connection name** | A descriptive name, e.g. `Lab VPN` |
| **Server name or address** | The public IP or hostname of the VPN server |
| **VPN type** | Select the appropriate protocol — e.g. L2TP/IPsec with pre-shared key |
| **Pre-shared key** | Enter the key configured on the server (for L2TP) |
| **Type of sign-in info** | Username and password |
| **Username / Password** | Credentials of a user account authorised on the VPN server |

4. Click **Save**

---

## Enabling MS-CHAP v2

MS-CHAP v2 is an authentication protocol commonly required by Windows VPN servers. It needs to be enabled under the connection's advanced options:

1. Go to **Settings → Network & Internet → VPN**
2. Click the VPN connection and select **Advanced options**
3. Click **Edit**
4. Under **VPN type**, ensure the protocol is set appropriately
5. Confirm MS-CHAP v2 is enabled as an authentication method

> **Note:** MS-CHAP v2 provides mutual authentication between the client and server, meaning both sides verify each other's identity during the connection handshake. While not the most modern protocol, it remains widely supported and is the default for Windows built-in VPN.

---

## Connecting

- Go to **Settings → Network & Internet → VPN**, select the connection, and click **Connect**
- Or click the network icon in the system tray, select the VPN connection from the list, and click **Connect**
- Enter credentials when prompted if not saved

---

## Verifying the Connection

Once connected, confirm the VPN tunnel is active:

```cmd
ipconfig /all
```

A new virtual network adapter (e.g. a PPP adapter) should appear with an IP address assigned from the VPN server's address pool, confirming the tunnel is established.

---

## Related Ticket

→ [TKT-018: Remote worker requires VPN access to connect securely to company resources](../tickets/TKT-019.md)