# Skill: Configuring Network Discovery

---

## What is Network Discovery?

Network discovery controls whether a device can see other devices on the network and whether other devices can see it. When enabled, the device appears in File Explorer under **Network** and can browse other discoverable devices on the same network. When disabled, the device is effectively hidden from the local network neighbourhood.

It is typically enabled on trusted networks (Private or Domain) and disabled on public networks where visibility to other devices is a security risk.

---

## Enabling Network Discovery

1. Open **Settings → Network & Internet → Advanced network settings → Advanced sharing settings**
2. Expand the relevant network profile (**Private** or **Domain**)
3. Toggle **Network discovery** to **On** — this also enables the option to allow the device to be found on the network
4. Optionally enable **Automatic setup of network connected devices** if device discovery for printers and other peripherals is needed

---

## Testing Network Discovery

From a second device on the same network:

- Open **File Explorer → Network** in the left sidebar
- The device should appear in the list of discoverable devices on the network
- If it does not appear immediately, wait a moment and click **Refresh** — network discovery can take a few seconds to propagate

> **Note:** Both devices need to have network discovery enabled and be on the same network profile for discovery to work in both directions. If the device still doesn't appear, confirm that the **Function Discovery Provider Host** and **Function Discovery Resource Publication** services are running in `services.msc` — these are required for network discovery to function.

---

## Related Ticket

→ [TKT-019: User's device not visible to other machines on the network](../tickets/TKT-020.md)
