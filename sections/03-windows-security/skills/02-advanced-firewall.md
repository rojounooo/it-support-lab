# Skill: Configuring Windows Firewall with Advanced Security

---

## Accessing Windows Firewall with Advanced Security

- Open the **Start Menu** and search for **Windows Defender Firewall with Advanced Security**
- Or run `Win + R` → type `wf.msc`

This opens the advanced console, distinct from the basic Windows Firewall settings in Settings → Privacy & Security. The advanced console allows granular control over inbound and outbound rules.

---

## Firewall Profiles

Windows Firewall applies different rule sets depending on which network profile is active. Understanding the profiles matters because a rule created under the wrong profile may not apply when expected.

| Profile | When It Applies |
|---------|-----------------|
| **Domain** | Active when the device is connected to a network where it can authenticate against a domain controller — typically a corporate network |
| **Private** | Active for trusted networks the user has manually marked as private — e.g. a home network |
| **Public** | Active for untrusted networks such as public Wi-Fi — most restrictive by default, blocks most inbound connections |

A device automatically switches profiles based on the network it connects to, and the relevant rule set is applied accordingly.

---

## Creating Rules via the GUI

### Inbound Rules

1. In the left pane, select **Inbound Rules**
2. In the right pane, click **New Rule**
3. Choose a rule type:
   - **Program** — restrict by executable path
   - **Port** — restrict by TCP/UDP port number
   - **Predefined** — use a built-in rule template (e.g. File and Printer Sharing)
   - **Custom** — combine multiple conditions
4. Follow the wizard to specify the program, port, or protocol
5. Choose to **Allow** or **Block** the connection
6. Select which profiles the rule applies to (Domain / Private / Public)
7. Name the rule descriptively and finish the wizard

### Outbound Rules

Follow the same process under **Outbound Rules**. Outbound rules are less commonly restricted by default, but are used when blocking specific applications from accessing the network.

---

## Creating Rules via PowerShell

PowerShell allows firewall rules to be created precisely and reproducibly, which reduces the chance of misconfiguration compared to manually working through the GUI wizard — particularly useful when the same rule needs to be deployed across multiple machines.

```powershell
New-NetFirewallRule -DisplayName "Allow RDP" `
  -Direction Inbound `
  -Protocol TCP `
  -LocalPort 3389 `
  -Action Allow `
  -Profile Domain,Private
```

| Parameter | Description |
|-----------|-------------|
| `-DisplayName` | Name shown in the GUI — should be descriptive |
| `-Direction` | `Inbound` or `Outbound` |
| `-Protocol` | `TCP` or `UDP` |
| `-LocalPort` | Port number the rule applies to |
| `-Action` | `Allow` or `Block` |
| `-Profile` | Which network profile(s) the rule applies to |

---

## Verifying a Rule

After creating a rule via PowerShell, it can be confirmed in the GUI:

- Open **Inbound Rules** (or Outbound Rules)
- Locate the rule by its display name
- Right-click → **Properties** to review or adjust its settings

This is a useful habit when scripting firewall changes — verify visually in the GUI that the rule was created with the intended scope before considering the task complete.

---

## Removing a Rule via PowerShell

```powershell
Remove-NetFirewallRule -DisplayName "Allow RDP"
```

---

## Related Ticket

→ [TKT-013: New application requires inbound port access — firewall rule configuration required](../tickets/TKT-013.md)