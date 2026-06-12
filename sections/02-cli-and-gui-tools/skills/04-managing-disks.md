# Skill: Managing and Optimising Disk Performance

Covers two built-in Windows tools for maintaining disk health and reclaiming storage space: Defragment and Optimise Drives, and Disk Cleanup.

---

## 1. Defragment and Optimise Drives

Over time, files on a disk can become fragmented — split across non-contiguous sectors — which slows read and write performance. The Optimise Drives tool analyses and defragments drives to improve efficiency.

> **Note:** Windows automatically optimises drives on a scheduled basis. This step is useful when troubleshooting performance issues or after a large number of files have been added or deleted.

> **Note:** SSDs do not benefit from defragmentation. Windows recognises SSDs and runs a TRIM operation instead, which is the appropriate optimisation for solid state drives.

### Steps

- Open the **Start Menu** and search for **Defragment and Optimise Drives**
- Select the drive to optimise from the list
- Click **Analyse** to check the current fragmentation level
- If fragmentation is above 10%, click **Optimise** to begin the process
- Wait for the operation to complete — this may take several minutes depending on drive size and fragmentation level

---

## 2. Disk Cleanup

Disk Cleanup removes temporary files, cached data, and other system files that are no longer needed, freeing up storage space.

### Steps

- Open the **Start Menu** and search for **Disk Cleanup**
- Select the drive to clean (typically `C:`) and click **OK**
- Windows will calculate how much space can be freed
- From the list of file categories, select the following at minimum:

| Category | Description |
|----------|-------------|
| Temporary files | Files created by apps that are no longer needed |
| Recycle Bin | Files pending permanent deletion |
| Temporary internet files | Cached browser and system data |
| Thumbnails | Cached image previews — rebuilt automatically when needed |

- Click **OK** and confirm to begin the cleanup

---

## 3. Optional — Additional Cleanup

### Remove Unused Programs

- Open **Settings → Apps → Installed Apps**
- Sort by size or last used date to identify candidates for removal
- Select any unused application and click **Uninstall**

### Remove Old Restore Points

Restore points can consume significant disk space over time. Keeping only the most recent point is sufficient for recovery purposes.

- In Disk Cleanup, click **Clean up system files**
- Select the **More Options** tab
- Under **System Restore and Shadow Copies**, click **Clean up**
- Confirm to remove all but the most recent restore point

---

## Related Ticket

>**Note:** No dedicated ticket — this skill is incorporated into [TKT-004: Device running slowly — health check and driver audit](../../01-os-installation/tickets/TKT-004.md)