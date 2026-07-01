# Skill: Deploying Software via Group Policy

Group Policy can be used to automatically deploy software to domain-joined computers without any manual intervention on the target machine. When the GPO applies, the software installs silently on next boot.

> **Note:** This method requires an MSI installer — `.exe` installers are not supported for GPO software deployment. If only an `.exe` is available, it must be repackaged into an MSI using a tool like Advanced Installer or wrapped using a transform file.

---

## Requirements

| Item | Details |
|------|---------|
| MSI installer | The software package to deploy, e.g. `Firefox.msi` |
| Network share | A shared folder on the DC or file server accessible by all target machines |
| GPMC | Group Policy Management Console installed on the managing machine |

---

## 1. Create a Network Share for the Software

Create a shared folder on the DC to host the installer:

```powershell
New-Item -ItemType Directory -Path "C:\SoftwareDeploy"
New-SmbShare -Name "Software" -Path "C:\SoftwareDeploy" -FullAccess "Domain Admins" -ReadAccess "Domain Computers"
```

Copy the MSI into the shared folder.

> **Note:** The share must be accessible by the **computer account** of target machines, not just user accounts — this is why `Domain Computers` needs read access. GPO software installation runs as the computer account during startup, before any user logs in.

---

## 2. Create the GPO

1. Open **Group Policy Management Console** (`gpmc.msc`)
2. Right-click the target OU and select **Create a GPO in this domain, and link it here**
3. Name it descriptively, e.g. `Deploy Firefox`
4. Right-click the GPO and select **Edit**

---

## 3. Configure Software Installation

1. Navigate to **Computer Configuration → Policies → Software Settings → Software Installation**
2. Right-click in the right pane and select **New → Package**
3. Browse to the MSI using the **UNC network path** — e.g. `\\DC01\Software\Firefox.msi`

> **Note:** The UNC path (`\\server\share\file.msi`) must be used rather than a local path (`C:\...`). The client machine resolves this path over the network when the policy applies — a local path on the DC would not be accessible from the client.

4. Select **Assigned** as the deployment method and click **OK**

| Deployment Method | Behaviour |
|------------------|-----------|
| **Assigned** | Software installs automatically on next boot — no user interaction required |
| **Published** | Software appears in Add/Remove Programs for the user to install manually |

---

## 4. Apply the Policy

On the target machine, force a policy refresh and restart:

```powershell
gpupdate /force
```

Then restart the machine. The software will install silently during the next startup as the GPO applies.

---

## 5. Verify

Log into the target machine after restart and confirm the software is installed via **Settings → Apps → Installed Apps** or by checking for the application in the Start Menu.

To confirm the GPO applied correctly:

```powershell
gpresult /r
```

The `Deploy Firefox` GPO should appear under **Applied Group Policy Objects**.

---
