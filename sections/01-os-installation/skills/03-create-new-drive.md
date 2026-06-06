# Skill: Installing and Configuring a New Drive on Windows 11

> **Note:** This guide was practised using VMs, but the steps reflect a standard physical installation.

---

## Requirements

| Item | Details |
|------|---------|
| Windows 11 Client | A PC with a spare drive slot available |
| New Drive | SSD or HDD to be installed |

---

## Steps

### 1. Install the Drive

- Power off the device and open the case
- Seat the drive in an available slot and secure it
- Connect the SATA data cable to the motherboard and the power cable from the PSU
- Power the device back on and boot into Windows

> **Note:** For VMs, attach a new virtual disk via the hypervisor settings before powering on the machine.

---

### 2. Open Disk Management

- Right-click the **Start** button and select **Disk Management**, or run `diskmgmt.msc` from the Run dialog (`Win + R`)
- The new drive will appear at the bottom of the window, labelled as **Unknown / Not Initialised**
- A prompt to initialise the disk may appear automatically — if not, right-click the disk and select **Initialise Disk**
- Select **GPT (GUID Partition Table)** as the partition style and confirm

> **Note:** GPT is the recommended partition style for modern systems and is required for drives larger than 2TB. MBR is legacy and used for older hardware compatibility.

---

### 3. Allocate Space

- Once initialised, the disk will show as **Unallocated**
- Right-click the unallocated space and select **New Simple Volume**
- Work through the wizard:

| Setting | Value |
|---------|-------|
| Volume size | Leave at maximum to use the full disk, or specify a size in MB |
| Drive letter | Assign an available letter, e.g. `D:` |
| File system | NTFS |
| Allocation unit size | Default |
| Volume label | Optional — e.g. `Data` or `Storage` |

- Complete the wizard and allow Windows to format the volume

---

### 4. Verify in File Explorer

- Open **File Explorer** (`Win + E`)
- The new drive should appear under **This PC** with the assigned drive letter and label
- The drive is now ready for use

---

## Related Ticket

→ [TKT-003: Additional hard drive fitted to a workstation needs initialising and partitioning before use](../tickets/TKT-003.md)