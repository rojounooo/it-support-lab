# Skill: User Profile Management on Windows 11

Covers creating a local user account, logging in for the first time, backing up the profile, deleting it, and restoring it from backup.

---

## Requirements

| Item | Details |
|------|---------|
| Windows 11 Client | Device to manage profiles on |
| Shared Folder / Network Location | Destination for profile backups |

---

## 1. Create a New Local User

- Open **Settings → Accounts → Other Users**
- Select **Add account**
- At the Microsoft account prompt, select **I don't have this person's sign-in information**
- On the next screen, select **Add a user without a Microsoft account**
- Enter a username, password, and security questions
- Click **Next** to create the account

The new user will now appear under **Other Users**.

---

## 2. Log Into the New Account

- Either **sign out** of the current user session via the Start Menu, or **restart** the device
- At the login screen, select the new user account and enter the password
- Windows will take a few minutes to set up the profile on first login — this is expected

> **Note:** The initial login creates the profile folder at `C:\Users\<username>`. The profile does not exist on disk until the user logs in for the first time.

---

## 3. Back Up the User Profile

### 3a. Create and Share a Backup Folder

- Create a folder to store profile backups, e.g. `C:\ProfileBackups`
- Right-click the folder and select **Properties → Sharing → Share**
- Add the relevant users or set to **Everyone** for lab purposes
- Enable network sharing and confirm

> **Note:** In a production environment, backups would typically be saved to a dedicated file server or NAS rather than a local shared folder. If the backup destination does not appear automatically during the backup process, use **Set on a network** to browse to it manually.

### 3b. Run Backup and Restore

- Open **Control Panel** and set the view to **Small Icons**
- Select **Backup and Restore (Windows 7)**
- Click **Set up backup**
- When prompted to choose a backup location, select the shared folder created in Step 3a
  - If the shared folder does not appear automatically, select **Save on a network** and browse to the share path (e.g. `\\HOSTNAME\ProfileBackups`)
- Select **Let me choose** when asked what to back up
- Navigate to and select `C:\Users\<username>` to include the full profile
- Confirm the backup settings and click **Save settings and run backup**

---

## 4. Delete the User Profile

- Open **Settings → System → About**
- Scroll down and select **Advanced system settings**
- Under the **Advanced** tab, go to **User Profiles → Settings**
- Select the profile to be removed from the list
- Click **Delete** and confirm

> **Note:** Deleting a profile here removes the profile data from `C:\Users`. The user account itself still exists and can be re-assigned a profile on next login. To fully remove the account, go back to **Settings → Accounts → Other Users** and select **Remove**.

---

## 5. Restore the User Profile from Backup

- Open **Control Panel → Small Icons → Backup and Restore (Windows 7)**
- Select **Restore my files**
- Click **Browse for files** or **Browse for folders** and navigate to the backup location on the shared drive
- Select the backed up profile folder and click **Add folder**
- Choose to restore files to their **original location**
- Click **Restore** and allow the process to complete

> **Note:** If restoring to a different device or a freshly created account, select **In the following location** and point it to `C:\Users\<username>` for the new account.

---

## Related Tickets

→ [TKT-006: New starter requires a local user account created and verified before first day](../tickets/TKT-006.md)  
→ [TKT-007: User's profile needs to be backed up ahead of a device refresh](../tickets/TKT-007.md)  
→ [TKT-008: User has left the organisation — profile to be removed from the device](../tickets/TKT-008.md)  
→ [TKT-009: User returning from leave needs their profile restored from backup](../tickets/TKT-009.md)