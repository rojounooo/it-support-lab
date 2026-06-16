# Skill: Managing System Resources with MMC Snap-ins

---

## What is MMC?

The Microsoft Management Console (MMC) is a centralised framework for hosting administrative tools in Windows. Rather than opening Event Viewer, Disk Management, Device Manager, and Task Scheduler as separate windows during a troubleshooting session, MMC lets you load all of them into a single interface called a **console**.

Each tool loaded into MMC is called a **snap-in** — a self-contained management module that plugs into the console. MMC itself does nothing on its own; its value is in the snap-ins added to it.

MMC also supports remote management — snap-ins can be pointed at another machine on the network, allowing you to manage a remote system without leaving your desk.

---

## Opening MMC

- Run `Win + R` → type `mmc`
- Or search **MMC** in the Start Menu
- Accept the UAC prompt — an empty console window will open

---

## Adding Snap-ins

1. Go to **File → Add/Remove Snap-in**
2. From the list of available snap-ins on the left, select the one you want to add
3. Click **Add**
4. When prompted, select **Local computer** to manage the local machine, or specify a remote computer name to manage another device on the network
5. Repeat for each snap-in needed
6. Click **OK** to load them into the console

---

## Useful Snap-ins for IT Support

| Snap-in | What it's used for |
|---------|-------------------|
| **Event Viewer** | View system, application, and security logs — first stop when diagnosing errors or crashes |
| **Disk Management** | Initialise, partition, and format drives without opening a separate utility |
| **Device Manager** | View hardware, check driver status, and update or roll back drivers |
| **Task Scheduler** | View, create, and manage scheduled tasks |
| **Performance Monitor** | Real-time and logged performance data for CPU, memory, disk, and network |

---

## Saving a Console

Once snap-ins are configured, the console can be saved as a `.msc` file for reuse:

- **File → Save As** → choose a location and name, e.g. `troubleshooting-console.msc`
- Double-clicking the saved file reopens the console with all snap-ins loaded

This is particularly useful for building a standardised troubleshooting console that can be shared across a support team or reused across machines.

---

## Notes

- MMC is most useful during active troubleshooting sessions where you need to cross-reference multiple tools simultaneously — for example, checking Event Viewer logs while monitoring Performance Monitor and verifying a driver in Device Manager, all without switching windows
- Individual snap-ins can still be launched directly (e.g. `eventvwr.msc`, `diskmgmt.msc`) when only one tool is needed