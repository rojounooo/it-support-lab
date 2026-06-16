# Skill: Analysing System Information and Resources

---

## System Information

System Information (`msinfo32`) provides a comprehensive snapshot of the hardware, components, and software environment on a Windows machine. It is useful for auditing a device, gathering specs before a repair or upgrade, or diagnosing conflicts.

### Accessing System Information

- Run `Win + R` → type `msinfo32`
- Or search **System Information** in the Start Menu

---

## Categories

### System Summary

The top-level overview of the machine. Displays OS version, build number, system manufacturer and model, processor, installed RAM, BIOS version, and Windows directory. This is usually the first place to check when you need a quick overview of a device.

---

### Hardware Resources

Low-level information about how hardware is interacting with the system:

| Subcategory | Description |
|-------------|-------------|
| **Conflicts / Sharing** | Lists any hardware resource conflicts — useful when a device is malfunctioning due to an IRQ or I/O conflict |
| **DMA** | Direct Memory Access channels in use |
| **Forced Hardware** | Devices with manually overridden settings |
| **I/O** | Input/output port addresses assigned to hardware |
| **IRQs** | Interrupt Request lines assigned to devices |
| **Memory** | Physical memory address ranges in use by hardware |

---

### Components

Detailed information about individual hardware components installed on the device, including display adapters, network adapters, storage devices, USB controllers, and more. Each component entry shows its driver version, status, and configuration — useful for identifying driver issues or confirming hardware specs before installing software.

---

### Software Environment

Information about the software state of the running system:

| Subcategory | Description |
|-------------|-------------|
| **System Drivers** | All drivers currently loaded, including status and type |
| **Environment Variables** | System and user environment variables (e.g. `PATH`, `TEMP`) |
| **Print Jobs** | Any documents currently in the print queue |
| **Network Connections** | Active network connections and their properties |
| **Running Tasks** | Processes currently running, similar to Task Manager but as a static snapshot |
| **Loaded Modules** | DLL files loaded by running processes |
| **Services** | All services and their current state |
| **Startup Programs** | Applications configured to run at startup |

---

## Resource Monitor

Resource Monitor provides a real-time, detailed view of how system resources are being consumed. It goes deeper than Task Manager by showing exactly which processes are using specific files, ports, and memory addresses.

### Accessing Resource Monitor

- Search **Resource Monitor** in the Start Menu
- Or open Task Manager → Performance tab → **Open Resource Monitor** at the bottom

---

## Resource Monitor Tabs

### Overview
A summary view showing CPU, disk, network, and memory usage side by side in real time. A good starting point before drilling into a specific resource.

### CPU
Shows per-process CPU usage broken down by thread, along with which services each process is associated with. Useful for identifying a specific thread or service driving high CPU usage.

### Memory
Displays physical memory usage across all processes. Shows committed, working set, shareable, and private memory per process — useful when diagnosing memory leaks or identifying processes consuming excessive RAM.

### Disk
Shows real-time disk read and write activity per process and per file. Useful for identifying what is causing high disk usage — for example, an application writing excessive logs or an indexing process running unexpectedly.

### Network
Displays active network connections per process, including the remote address and port being used. Useful for identifying unexpected outbound connections or diagnosing which application is consuming bandwidth.