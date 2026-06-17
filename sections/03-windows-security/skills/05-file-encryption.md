# Skill: Configuring the Encrypting File System (EFS)

EFS is a built-in Windows feature that encrypts individual files and folders on an NTFS volume, tied to the user account that performed the encryption. Only that user (or a designated recovery agent) can decrypt and open the file.

---

## Creating a Test File via PowerShell

### 1. Create a Variable Holding a Short String

```powershell
$content = "This is a test file for EFS encryption."
```

### 2. Set the File Path

```powershell
$filepath = "$env:USERPROFILE\Documents\efs-test.txt"
```

### 3. Write the Content to the File

```powershell
$content | Out-File -FilePath $filepath
```

This creates `efs-test.txt` in the user's Documents folder containing the string defined above.

---

## Checking EFS is Enabled

```cmd
fsutil behavior query disableencryption
```

> **Note:** This checks whether EFS is disabled at the system level. A return value of `0` means encryption is **enabled** (not disabled), and a value of `1` means EFS has been disabled system-wide. This is worth checking before attempting to encrypt a file, since some organisations disable EFS via Group Policy.

---

## Encrypting the File

```cmd
cipher /e $filepath
```

`cipher` is the command-line utility for managing EFS. The `/e` flag encrypts the specified file or directory. Once encrypted, the file is marked with an EFS attribute — visible in File Explorer as the filename appearing in green text (default behaviour) — and can only be opened by the user account that encrypted it, using their EFS certificate.

---

## Certificate Manager (certmgr.msc)

When a file is encrypted with EFS for the first time, Windows automatically generates an EFS certificate and stores it in the user's personal certificate store. This certificate (and its associated private key) is what allows the file to be decrypted — without it, the encrypted file is unreadable, even by an administrator.

### What Certificate Manager Is

Certificate Manager is a snap-in for viewing and managing digital certificates issued to and trusted by the current user, including personal certificates, trusted root authorities, and intermediate certificates.

### Accessing Certificate Manager

- Run `Win + R` → type `certmgr.msc`

### Exporting the EFS Certificate

1. Navigate to **Personal → Certificates**
2. Locate the certificate issued to the current user for EFS
3. Right-click the certificate → **All Tasks → Export**
4. Select **Yes, export the private key** — this is essential, as the private key is required to decrypt files later
5. Choose **Personal Information Exchange (.pfx)** format
6. Set a password to protect the exported file
7. Save the `.pfx` file to a secure, backed-up location — ideally off the device itself

> **Note:** Exporting and securely storing the EFS certificate is critical. If the original user profile is lost, corrupted, or the certificate is otherwise removed, any EFS-encrypted files become permanently unreadable without this backup. This is one of the most common real-world EFS support issues — a user reformats their machine without exporting the certificate first, and loses access to their own encrypted files.

---

## Related Ticket

→ [TKT-016: User requests sensitive files be encrypted on local device](../tickets/TKT-016.md)