# Skill: Configuring File and Printer Sharing

---

## Enabling File and Printer Sharing

1. Open **Settings → Network & Internet → Advanced network settings → Advanced sharing settings**
2. Expand the relevant network profile (Private or Domain)
3. Toggle **File and printer sharing** to **On**

> **Note:** File and printer sharing should only be enabled on trusted network profiles (Private or Domain). Enabling it on a Public profile exposes shared resources to any device on the network, which is a security risk on untrusted networks such as public Wi-Fi.

---

## Sharing a Folder

1. Create or locate the folder to share (e.g. `C:\SharedFiles`)
2. Right-click the folder → **Properties → Sharing tab → Share**
3. Type `Everyone` in the search field and click **Add**
4. Set the permission level — **Read** for view-only access, **Read/Write** to allow modifications
5. Click **Share** to confirm

---

## Accessing a Shared Folder

From another device on the same network, the shared folder can be accessed by:

- Opening **File Explorer** and navigating to `\\HOSTNAME\SharedFiles`
- Or mapping it as a network drive via `net use` (covered in [Section 2 — CLI Networking](../../02-cli-and-gui-tools/skills/04-cli-networking.md))

---

## Note on Permissions

Sharing a folder to **Everyone** via the Sharing tab grants access at the **share permissions** level. For tighter access control, NTFS permissions should be configured alongside share permissions — covered in [Section 3 — Manage NTFS Permissions](../../03-windows-security/skills/06-ntfs-permissions.md).

---

## Related Ticket

No dedicated ticket — the folder sharing workflow is covered in [TKT-007: User profile backup ahead of device refresh](../../01-os-installations/tickets/TKT-007.md), which uses a shared folder as the backup destination.