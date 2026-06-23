# Skill: Mapping Network Drives

Mapping a network drive assigns a drive letter to a shared network folder, making it accessible in File Explorer alongside local drives. This is common in business environments where shared folders are used for team files, backups, or department resources.

---

## Mapping a Drive via File Explorer

1. Open **File Explorer** and click **This PC** in the left sidebar
2. Click the **three-dot menu** (or right-click an empty area) and select **Map network drive**
3. Fill in the fields:

| Field | Value |
|-------|-------|
| **Drive** | Select an available drive letter, e.g. `Z:` |
| **Folder** | Enter the UNC path to the shared folder, e.g. `\\HOSTNAME\SharedFiles` |
| **Reconnect at sign-in** | Tick to automatically reconnect the drive on every login |
| **Connect using different credentials** | Tick if the share requires credentials different from the current logged-in user |

4. Click **Finish**

The mapped drive will appear under **This PC** in File Explorer alongside local drives.

---

## Testing the Mapped Drive

1. Open the mapped drive in File Explorer
2. Create a folder and a test file inside it
3. From a second machine on the same network, navigate to `\\HOSTNAME\SharedFiles` in File Explorer and confirm the folder and file are visible
4. This confirms the share is accessible over the network and the permissions are configured correctly

---

## Disconnecting a Mapped Drive

- Right-click the drive in File Explorer → **Disconnect**
- Or via command line: `net use Z: /delete`

---

## Note on Persistence

Mapped drives are tied to the user profile — they are visible only to the user who mapped them and reconnect at login only for that user. In a domain environment, network drives are typically pushed to all users automatically via Group Policy rather than mapped individually, which is covered in Section 5.

---

## Related Ticket

No dedicated ticket — drive mapping via the command line is demonstrated in [Section 2 — CLI Networking](../../02-cli-and-gui-tools/skills/04-cli-networking.md) using `net use`.