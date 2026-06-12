# Skill: Task Manager 

Task Manager is a built-in Windows utility for monitoring system performance, managing running processes, and diagnosing resource issues.

---

## Accessing Task Manager

| Method | Steps |
|--------|-------|
| Keyboard shortcut | `Ctrl + Shift + Esc` |
| Right-click taskbar | Right-click the taskbar → Task Manager |
| Run dialog | `Win + R` → type `taskmgr` |
| Ctrl + Alt + Delete | Select Task Manager from the menu |

---

## Tabs Overview

### Processes
Shows all running applications and background processes. Displays real-time CPU, memory, disk, and network usage per process. Right-click any process to end it, open its file location, or search online for more information.

---

### Performance
Displays live graphs for overall CPU, memory, disk, network, and GPU usage. Useful for identifying resource bottlenecks — for example, high CPU usage at idle, or memory running close to capacity. Click **Open Resource Monitor** at the bottom for a more detailed breakdown.

---

### App History
Shows cumulative CPU and network usage per application over time. Primarily relevant for Microsoft Store apps. Useful for identifying apps consuming excessive resources in the background.

---

### Startup Apps
Lists all applications configured to launch at startup, along with their impact rating (Low / Medium / High). Right-click any entry to enable or disable it. Disabling high-impact startup apps is a common first step when troubleshooting slow boot times.

---

### Users
Shows all logged-in user sessions and their resource consumption. Useful on shared machines to identify which session is consuming the most resources.

---

### Details
A more granular view of all running processes, showing PID, status, CPU and memory usage, and the user account running each process. Commonly used when a specific process needs to be identified by its PID or terminated forcefully.

---

### Services
Lists all Windows services and their current status (Running / Stopped). Right-click any service to start, stop, or restart it. For more detailed service management, open `services.msc` directly.

>**Note:** No ticket for this skill as it's just an overview