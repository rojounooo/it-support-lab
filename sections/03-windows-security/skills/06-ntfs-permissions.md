# Skill: Managing NTFS Permissions

NTFS permissions control which users and groups can access a file or folder, and what level of access they have. Unlike share permissions (which apply only over the network), NTFS permissions apply regardless of how the file is accessed — locally or remotely — and are generally the more granular and important layer to configure correctly.

---

## Setting Permissions on a Folder

### 1. Create the Folder

Create the target folder, e.g. `C:\RemoteAccessData`.

### 2. Open Properties

Right-click the folder → **Properties**.

### 3. Go to the Security Tab

Select the **Security** tab — this lists all users and groups currently with permissions on the folder, along with their access level.

### 4. Edit Permissions

Click **Edit** to open the editable permissions window.

### 5. Add the Relevant Group

- Click **Add**
- Enter the group name (e.g. `Remote Access Users`) and click **Check Names** to validate it
- Click **OK** to add the group to the permissions list

### 6. Set Permission Levels

With the group selected, tick the appropriate permission level under the **Allow** column:

| Permission | Grants |
|------------|--------|
| **Full Control** | Read, write, modify, delete, and change permissions on the folder |
| **Modify** | Read, write, and delete files, but cannot change permissions |
| **Read & Execute** | View and run files, but cannot make changes |
| **Read** | View files only |
| **Write** | Add files and write data, but not necessarily view existing content depending on combination with other permissions |

Click **Apply**, then **OK** to confirm.

---

## Removing Default Access

By default, broader groups such as **Users** or **Everyone** may already have access to a new folder depending on its parent directory's inherited permissions. To restrict a folder to only the intended group:

- In the Security tab, select the group to remove (e.g. **Users**)
- Click **Remove**

> **Note:** If permissions appear greyed out and cannot be removed, the folder is inheriting permissions from its parent directory. Click **Advanced → Disable Inheritance** first, then choose to convert inherited permissions to explicit ones or remove them entirely before editing.

---

## Verifying Access

- Log in as a user belonging to the permitted group and confirm the folder is accessible
- Log in as (or simulate) a user **not** in the group and confirm access is denied

---

## Related Ticket

→ [TKT-017: Folder required that is only accessible to Remote Access Users](../tickets/TKT-017.md)