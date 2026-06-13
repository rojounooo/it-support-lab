# Skill: Managing the Windows Registry

---

## What is the Registry?

The Windows Registry is a centralised hierarchical database that stores configuration settings and options for the operating system, hardware, installed applications, and user preferences. When software is installed, when a user changes a system setting, or when Windows itself initialises, it reads from and writes to the registry.

It is one of the most sensitive areas of a Windows system — incorrect changes can cause applications to malfunction or prevent Windows from booting.

> **Warning:** Always export a backup of any registry key before modifying it. There is no undo function in Registry Editor.

---

## Accessing Registry Editor

- Run `Win + R` → type `regedit`
- Accept the UAC prompt to open with administrator privileges

---

## Registry Structure

The registry is organised into five root keys, each storing a different category of settings:

| Root Key | Abbreviation | Contains |
|----------|-------------|----------|
| HKEY_CLASSES_ROOT | HKCR | File associations and COM object registrations |
| HKEY_CURRENT_USER | HKCU | Settings and preferences for the currently logged-in user |
| HKEY_LOCAL_MACHINE | HKLM | System-wide settings for hardware and software, applies to all users |
| HKEY_USERS | HKU | Settings for all user profiles on the machine |
| HKEY_CURRENT_CONFIG | HKCC | Hardware profile information used at startup |

---

## Exporting a Registry Key (Backup)

Before making any changes to a registry key, export it as a backup so it can be restored if something goes wrong.

1. In Registry Editor, navigate to the key you want to back up
2. Right-click the key and select **Export**
3. Choose a save location and give the file a descriptive name, e.g. `HKLM-Software-backup-2026-01-01`
4. Ensure **Selected branch** is chosen and click **Save**

This saves the key and all its subkeys as a `.reg` file.

---

## Restoring a Registry Key from Backup

1. Navigate to the `.reg` backup file in File Explorer
2. Double-click the file and confirm the UAC prompt
3. Confirm the prompt asking whether to add the information to the registry
4. The key and its values will be restored

---

## Notes

- Registry changes take effect immediately in most cases, though some changes require a restart or a user log-off to apply
- The registry can also be edited remotely on another machine via **File → Connect Network Registry**, provided the Remote Registry service is running on the target machine and appropriate permissions are in place