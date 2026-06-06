# Skill: Restore Windows 11 after system file corruption 

> **Note:** This guide assumes the deletion of a System32 file, only test on VMs or a system you are authorised to use. 

---

## Requirements

| Item | Details |
|------|---------|
| Windows 11 Client | A file will be deleted from System32 preventing automatic repair|

---

## Steps

### 1. Advanced Options 
- When automatic repair fails there are 2 options: 
    - Shut Down 
    - Advanced Options 

Select advanced options 

### 2. Troubleshoot 

Select the troubleshoot option from the list

### 3. Reset PC 
- There are 2 options: 
    - Keep my files (keeps personal files removes all others)
    - Remove everything (clean install equivalent)

Select keep my files as a corrupted windows install doesn't need a clean reinstall 

### 4. Cloud Download 
- Requires an internet connection 

Choose cloud download to reinstall 

--- 

## Related Ticket

→ [TKT-002: User's PC fails to boot — automatic repair unsuccessful, manual recovery required](../tickets/TKT-002.md)