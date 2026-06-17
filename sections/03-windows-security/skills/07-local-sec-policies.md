# Skill: Configuring Local Security Policy

---

## What is Local Security Policy?

Local Security Policy (`secpol.msc`) is a Windows management console used to configure security settings on a local machine — password requirements, account lockout behaviour, and audit logging. It applies only to the device it is configured on.

> **Note:** This tool manages settings for **local** accounts only. In a managed environment, these same controls are typically enforced centrally rather than per-device — via **Configuration Profiles in Microsoft Intune** for cloud-managed devices, or via **Group Policy in Active Directory** for on-premises domain-joined devices. Local Security Policy is most relevant for standalone machines or for understanding what a centrally pushed policy is actually configuring under the hood.

### Accessing Local Security Policy

- Open the **Start Menu** and search for **Local Security Policy**
- Or run `Win + R` → type `secpol.msc`

---

## Password Policy

Located under **Account Policies → Password Policy**.

| Setting | Description |
|---------|-------------|
| **Enforce password history** | Number of previous passwords remembered, preventing reuse. Setting this to `15` means a user cannot reuse any of their last 15 passwords. |
| **Maximum password age** | Number of days before a password expires and must be changed |
| **Minimum password age** | Number of days that must pass before a password can be changed again — prevents a user from immediately reverting to a previous password to bypass history |
| **Minimum password length** | Minimum number of characters required |
| **Password must meet complexity requirements** | When enabled, requires passwords to include a mix of uppercase, lowercase, numbers, and symbols |

---

## Account Lockout Policy

Located under **Account Policies → Account Lockout Policy**.

| Setting | Description |
|---------|-------------|
| **Account lockout threshold** | Number of failed login attempts before the account is locked — e.g. setting this to `3` locks the account after 3 invalid attempts |
| **Account lockout duration** | How long the account remains locked before automatically unlocking |
| **Reset account lockout counter after** | How long after a failed attempt before the failed attempt counter resets to zero |

> **Note:** Locking out an account after a low number of attempts (e.g. 3) reduces the risk of brute-force password attacks, but setting it too low can increase helpdesk tickets from legitimate users locking themselves out through typos.

---

## Audit Policy

Located under **Local Policies → Audit Policy**.

Audit policies determine which security-related events are logged to the Security log in Event Viewer. Each policy can be set to audit **Success**, **Failure**, or both.

| Policy | What It Logs |
|--------|-------------|
| **Audit account logon events** | Logon attempts validated against local account credentials |
| **Audit account management** | Creation, modification, or deletion of user and group accounts |
| **Audit logon events** | Local logon and logoff events |
| **Audit object access** | Access to specific files, folders, or objects that have auditing configured on them |
| **Audit policy change** | Changes made to security policy settings themselves |

> **Note:** Enabling **Audit account logon events** with **Failure** auditing is particularly useful for incident response — a spike in failed logon attempts for a specific account is a strong indicator of a brute-force attempt or a compromised credential being tested. These events appear in the Security log in Event Viewer and can be cross-referenced with the account lockout policy to understand the full picture of an attempted intrusion.

---
