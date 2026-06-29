# Skill: Password Reset, Account Unlock, and Forced Password Change in Active Directory

---

## Security Implications
- Always confirm the users identity as this could be a potential attack by a malicious actor

## Reset a User's Password

```powershell
Set-ADAccountPassword -Identity "jsmith" -Reset -NewPassword (ConvertTo-SecureString "NewTempPassword123!" -AsPlainText -Force)
```

> **Note:** The `-Reset` flag replaces the existing password entirely rather than requiring the old password to be provided first — necessary when the user has forgotten their password.

---

## Force Password Change at Next Logon

```powershell
Set-ADUser -Identity "jsmith" -ChangePasswordAtLogon $true
```

Ensures the user sets their own password on first login rather than continuing to use the temporary one set by the admin.

---

## Unlock a Locked Account

```powershell
Unlock-ADAccount -Identity "jsmith"
```

An account becomes locked when the number of failed login attempts exceeds the threshold defined in the domain's account lockout policy. The account remains locked until an admin unlocks it or the lockout duration expires. This is one of the most common helpdesk tickets in an AD environment.

---

## Verify Account Status

```powershell
Get-ADUser -Identity "jsmith" -Properties LockedOut, PasswordExpired, PasswordLastSet
```

---

## Related Ticket

→ [TKT-022: User account locked out and password reset required](../tickets/TKT-022.md)