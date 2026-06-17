# Skill: Configuring User Account Control (UAC) Levels

---

## What is UAC?

User Account Control is a Windows security feature that prompts for permission or an administrator password before allowing changes that could affect the system — installing software, modifying system settings, or running an application with elevated privileges. It exists to prevent malicious software (and accidental user actions) from making changes without the user being aware.

---

## Accessing UAC Settings

- Open the **Start Menu** and search for **Change User Account Control Settings**, or **UAC**

This opens a single window with a vertical slider controlling the notification level.

---

## UAC Levels

| Level | Behaviour |
|-------|-----------|
| **Always notify** | Prompts for every action that requires elevation, and dims the desktop while waiting for a response. The most secure and most intrusive setting. |
| **Notify me only when apps try to make changes to my computer (default)** | Prompts when an application attempts to make changes, but not when the user changes Windows settings directly. The default and recommended balance between security and usability. |
| **Notify me only when apps try to make changes to my computer (do not dim my desktop)** | Same as default, but skips the secure desktop dimming — faster, but slightly less secure as it does not isolate the prompt from the rest of the desktop. |
| **Never notify** | Disables UAC prompts entirely. Applications can make changes without any confirmation. Not recommended outside of specific testing or legacy software scenarios. |

---

## Managing UAC via PowerShell

UAC's notification level is stored in the registry under `HKEY_LOCAL_MACHINE`, which holds system-wide settings that apply to all users on the device — appropriate for UAC, since it is a machine-level security policy rather than a per-user preference.

### Check Whether UAC is Enabled

```powershell
Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" -Name EnableLUA
```

`EnableLUA` controls whether UAC is enabled at all:

| Value | Meaning |
|-------|---------|
| `1` | UAC enabled |
| `0` | UAC disabled |

---

### Enable or Disable UAC

```powershell
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" -Name EnableLUA -Value 0
```

> **Note:** This disables UAC entirely rather than adjusting the notification level — there is no prompt of any kind once `EnableLUA` is set to `0`. A restart is required for the change to take effect, the same as toggling UAC off via the GUI slider's lowest position.

---

## Related Ticket

→ [TKT-015: User requests UAC level changed due to repeated elevation prompts during routine work](../tickets/TKT-015.md)