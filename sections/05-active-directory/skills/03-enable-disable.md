# Skill: Disable and Enable User Accounts in Active Directory

---

## Disable a User Account

```powershell
Disable-ADAccount -Identity "jsmith"
```

> **Note:** Disabling an account prevents login without deleting the account or its group memberships. This is the recommended approach when a user leaves the organisation or an account needs to be suspended — it can be reversed instantly with `Enable-ADAccount`, unlike deletion.

---

## Enable a User Account

```powershell
Enable-ADAccount -Identity "jsmith"
```

---

## Verify Account Status

```powershell
Get-ADUser -Identity "jsmith" -Properties Enabled
```

Returns `Enabled : False` when disabled and `Enabled : True` when enabled.

---

## Verify Login

To confirm a disabled account cannot authenticate, attempt to start a process using its credentials:

```powershell
$username = "lab.internal\jsmith"
$password = ConvertTo-SecureString "CorrectPassword123!" -AsPlainText -Force
$credential = New-Object System.Management.Automation.PSCredential($username, $password)

Start-Process cmd -Credential $credential
```

A disabled account will fail to authenticate even with the correct password, confirming the disable is in effect. Re-enable the account and repeat to confirm login succeeds.

---

## Related Ticket

→ [TKT-023: User account requires disabling following departure from the organisation](../tickets/TKT-023.md)