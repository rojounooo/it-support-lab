# Skill: Moving a User Between Organisational Units in Active Directory

---

## Create the Destination OU

```powershell
New-ADOrganizationalUnit -Name "HR" -Path "DC=lab,DC=internal"
```

---

## Move the User

```powershell
Move-ADObject -Identity "CN=Jane Smith,OU=IT Support Lab,DC=lab,DC=internal" -TargetPath "OU=HR,DC=lab,DC=internal"
```

| Parameter | Description |
|-----------|-------------|
| `-Identity` | The full Distinguished Name (DN) of the user object to move |
| `-TargetPath` | The DN of the destination OU |

> **Note:** The Distinguished Name (DN) uniquely identifies an object in Active Directory by its full path through the directory tree. `CN` is the Common Name (the object itself), and each `OU` and `DC` component represents a step up the hierarchy. If you are unsure of a user's full DN, retrieve it with `Get-ADUser -Identity "jsmith" -Properties DistinguishedName`.

---

## Verify the Move

```powershell
Get-ADUser -Identity "jsmith" -Properties DistinguishedName | Select-Object DistinguishedName
```

The returned DN should now reflect the HR OU path rather than IT Support Lab.

---

## Related Ticket

→ [TKT-025: User transferred to HR department — Active Directory account requires moving to HR OU](../tickets/TKT-025.md)