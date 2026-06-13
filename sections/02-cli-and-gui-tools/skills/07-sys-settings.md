# Skill: Configuring System Settings with the System Configuration Utility

The System Configuration Utility (`msconfig`) is a built-in Windows tool for managing startup behaviour, boot options, and background services. It is commonly used for troubleshooting startup issues and performing clean boots.

---

## Accessing msconfig

- Run `Win + R` → type `msconfig`
- Or search **System Configuration** in the Start Menu

> **Note:** A restart is required for any changes made in msconfig to take effect.

---

## Tabs

### General

Controls how Windows loads at startup. Three options are available:

| Option | Behaviour |
|--------|-----------|
| **Normal Startup** | Loads all drivers, services, and startup programs — the default Windows behaviour |
| **Diagnostic Startup** | Loads only basic drivers and services — useful for isolating whether a core Windows component is causing an issue |
| **Selective Startup** | Allows manual control over which components load — used to perform a clean boot by deselecting startup items and non-Microsoft services |

---

### Boot

Manages boot configuration, primarily useful on machines running multiple operating systems.

| Setting | Description |
|---------|-------------|
| **Timeout** | How long the boot menu is displayed before the default OS loads automatically |
| **Safe Boot — Minimal** | Loads Windows in Safe Mode with only essential services and a basic GUI |
| **Safe Boot — Network** | Safe Mode with networking enabled |
| **No GUI Boot** | Suppresses the Windows loading animation during startup |
| **OS Boot Information** | Displays driver names as they load during startup — useful for identifying a driver causing a hang |

---

### Services

Lists all Windows services and third-party services configured to run at startup. Each can be individually enabled or disabled.

- **Hide all Microsoft services** checkbox — filters the list to show only third-party services, making it easier to identify software that may be causing conflicts
- Disabling services here and restarting performs a **clean boot** — a minimal environment used to rule out software conflicts as the cause of an issue

> **Note:** A clean boot is not the same as Safe Mode. Safe Mode uses a fixed minimal set of Microsoft drivers. A clean boot uses the normal Windows environment but with third-party services and startup items disabled, making it easier to identify a specific conflicting application.

---

### Startup

In Windows 10 and 11 this tab no longer manages startup items directly — it instead opens **Task Manager → Startup Apps**, where startup applications can be enabled or disabled.

---

### Tools

Lists a collection of built-in Windows administrative tools that can be launched directly from msconfig, including:

- Command Prompt
- Event Viewer
- Performance Monitor
- Registry Editor
- System Information
- UAC Settings

This tab is a convenience launcher — each tool is accessible independently, but having them in one place is useful during troubleshooting sessions.

---

## Related Ticket

→ [TKT-011: User reports application conflicts and system instability — clean boot required to isolate cause](../tickets/TKT-011.md)