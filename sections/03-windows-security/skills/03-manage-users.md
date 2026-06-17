# Skill: Managing Local User Accounts

---

## lusrmgr.msc — Local Users and Groups

`lusrmgr.msc` is a pre-built MMC snap-in dedicated to managing local user accounts and groups on a Windows machine.

### Accessing lusrmgr

- Run `Win + R` → type `lusrmgr.msc`

### Layout

| Folder | Shows |
|--------|-------|
| **Users** | All local user accounts on the device |
| **Groups** | All local groups, including built-in groups such as Administrators and Users |

---

## Creating a User via the GUI

1. Right-click **Users** → **New User**
2. Fill in the fields:
   - **User name**
   - **Full name**
   - **Password** — set a temporary password
   - Tick **User must change password at next logon**
3. Click **Create**

The temporary password combined with the must-change-at-next-logon flag ensures the user sets their own password on first login rather than continuing to use one the admin knows.

---

## Creating a User via PowerShell

```powershell
$Password = ConvertTo-SecureString "TempPassword123!" -AsPlainText -Force
New-LocalUser -Name "jsmith" -FullName "Jane Smith" -Password $Password -PasswordNeverExpires:$false
```

> **Note:** PowerShell requires passwords to be passed as a `SecureString` rather than plain text. `ConvertTo-SecureString` handles this conversion. The `-AsPlainText -Force` flags are required when converting a plain text string directly — in a script this is acceptable for setup, but the variable should not be left exposed afterward.

> **Note:** `New-LocalUser` does not have a parameter for **must change password at next logon** — this setting was configured via the GUI in `lusrmgr.msc` instead, by right-clicking the newly created user, selecting **Properties**, and ticking **User must change password at next logon**.

---

## Confirming the User Was Created

Switch back to `lusrmgr.msc` and refresh the view — either click **Groups** then back to **Users**, or close and reopen the console. The new account should now appear in the Users list.

---

## Managing Groups and Group Membership

### Via GUI

1. Open **Groups**, double-click the group to modify (e.g. **Administrators**)
2. Click **Add**, enter the username, and click **OK**

### Via PowerShell

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "jsmith"
Remove-LocalGroupMember -Group "Administrators" -Member "jsmith"
Get-LocalGroupMember -Group "Administrators"
```

---

## Disabling a Local User Account

```powershell
Disable-LocalUser -Name "jsmith"
```

> **Note:** Disabling an account prevents it from being used to log in, but does not delete the account, its profile data, or its group memberships. This is the recommended approach when a user leaves temporarily or an account needs to be suspended pending investigation, as it can be reversed instantly with `Enable-LocalUser`, unlike deletion which is not easily undone.

```powershell
Enable-LocalUser -Name "jsmith"
```

---

## Related Ticket

→ [TKT-014: New user account required with enforced password change on first login](../tickets/TKT-014.md)