# Skill: Managing Active Directory Group Membership

---

## Add a User to a Group

```powershell
Add-ADGroupMember -Identity "IT Support" -Members "jsmith"
```

---

## Remove a User from a Group

```powershell
Remove-ADGroupMember -Identity "IT Support" -Members "jsmith" -Confirm:$false
```

> **Note:** `-Confirm:$false` skips the confirmation prompt — useful when scripting bulk changes. Omit it when running manually if you want to confirm before each removal.

---

## Verify Group Membership

```powershell
Get-ADGroupMember -Identity "IT Support"
```

Returns all current members of the group. Confirm the added user appears and the removed user does not.

---

## Lab Scenario

Create a test user, add them to the IT Support group, confirm membership, then remove them and confirm they are no longer listed:

```powershell
# Create test user
New-ADUser -Name "Test User" -SamAccountName "testuser" -Path "OU=IT Support Lab,DC=lab,DC=internal" -AccountPassword (ConvertTo-SecureString "TempPassword123!" -AsPlainText -Force) -Enabled $true

# Add to group
Add-ADGroupMember -Identity "IT Support" -Members "testuser"

# Verify
Get-ADGroupMember -Identity "IT Support"

# Remove from group
Remove-ADGroupMember -Identity "IT Support" -Members "testuser" -Confirm:$false

# Verify removal
Get-ADGroupMember -Identity "IT Support"
```

---

## Related Ticket

→ [TKT-024: New IT support employee requires group access — departing employee requires removal](../tickets/TKT-024.md)