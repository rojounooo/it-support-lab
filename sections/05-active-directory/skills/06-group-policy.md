# Skill: Applying Basic Group Policy Using GPMC

---

## What is Group Policy?

Group Policy is a feature of Active Directory that allows administrators to centrally manage and enforce settings across users and computers in a domain. Settings are defined in a **Group Policy Object (GPO)** and linked to a site, domain, or OU — all objects within that container inherit the policy automatically.

Common uses include restricting access to system settings, enforcing security baselines, mapping network drives, and deploying software.

---

## Accessing the Group Policy Management Console

- Open the **Start Menu** and search for **Group Policy Management**
- Or run `Win + R` → type `gpmc.msc`

The console displays the domain structure — domains, OUs, and any existing GPOs linked to them.

---

## Creating a New GPO

1. In the left pane, expand the domain and right-click the OU the policy should apply to
2. Select **Create a GPO in this domain, and link it here**
3. Give the GPO a descriptive name, e.g. `Restrict Control Panel` and click **OK**

---

## Editing the GPO

1. Right-click the newly created GPO and select **Edit**
2. This opens the **Group Policy Management Editor**, where settings are organised under two categories:

| Category | Applies to |
|----------|-----------|
| **Computer Configuration** | Settings applied to the computer regardless of who logs in |
| **User Configuration** | Settings applied to the user regardless of which computer they log into |

3. Navigate to the relevant policy path and configure the setting
4. Close the editor when done — changes are saved automatically

---

## Linking a GPO to an OU

If the GPO was not linked during creation it can be linked afterward:

1. Right-click the target OU in GPMC
2. Select **Link an Existing GPO**
3. Select the GPO from the list and click **OK**

---

## Forcing a Policy Update

By default, Group Policy refreshes automatically every 90 minutes. To apply a policy immediately on a target machine:

```powershell
gpupdate /force
```

---

## Verifying a Policy is Applied

To confirm which policies are applied to the current user and machine:

```powershell
gpresult /r
```

For a detailed HTML report:

```powershell
gpresult /h C:\gpresult.html
```

Open the HTML file to see a full breakdown of applied GPOs, their source, and any that were filtered or blocked.

> **Note:** GPOs are processed in order — Local, Site, Domain, OU (LSDOU). A policy set at the OU level takes precedence over one set at the domain level. If a policy does not appear to apply as expected, check for conflicts or blocking inheritance higher up the hierarchy using `gpresult`.