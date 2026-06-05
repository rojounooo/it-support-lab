# IT Support Skills Lab

A hands-on IT support lab built alongside the [IT Support Technical Skills Bootcamp](https://www.udemy.com/course/it-support-technical-skills-training-part-1/) by Jobskillshare. Each section of the course is translated into practical, documented work: a skill reference, a realistic support ticket, and a recorded resolution — all managed through a live ticketing system.

The goal isn't just to follow a course. It's to simulate what first-line IT support actually looks like on the job — receiving a request, working through it methodically, and documenting the outcome.

---

## Why This Project

Most IT support courses teach you *what* to do. This project focuses on *how it looks in practice* — tickets raised, steps taken, and resolutions recorded in the same way a real support team would expect.

Each topic from the course maps to a ticket in one of the ticketing systems. The skill documentation covers the technical steps; the ticket covers the user-facing scenario. Together they form a complete picture of both the technical knowledge and the support workflow behind it.

This is also a deliberate response to a common gap in IT job applications: having theoretical knowledge but no evidence of working within a support process. This lab is the evidence.

---

## What's Covered

| # | Section | Focus |
|---|---------|-------|
| 01 | Operating System Installations & Upgrades | Clean installs, in-place upgrades, hardware compatibility |
| 02 | Windows Command-Line & Graphical Management Tools | CMD, PowerShell, MMC, Task Manager, Event Viewer |
| 03 | Windows Security Controls | User accounts, UAC, BitLocker, Windows Defender, firewall |
| 04 | Windows Networking Configuration | IP addressing, DNS, DHCP, network adapters, connectivity troubleshooting |
| 05 | Active Directory & Group Policy | User/group management, OUs, GPO creation and application |
| 06 | Inventory & Asset Management Systems | Asset tracking, hardware audits, CMDB concepts |
| 07 | Software Installation & Deployment | Manual installs, package managers, silent deployment |
| 08 | Office 365 Administration | User provisioning, licensing, mailbox management, SharePoint basics |
| 09 | Azure Management Skills | Azure AD, resource groups, virtual machines, RBAC |

---

## Repo Structure

```
it-support-lab/
├── README.md
├── ticketing/
│   ├── freshdesk-setup.md
│   ├── servicenow-setup.md
│   └── jira-setup.md            # Freshdesk, ServiceNow and Jira Service Management setup
├── sections/
│   ├── 01-os-installations/
│   │   ├── README.md               # Section overview
│   │   ├── skills/                 # Technical how-to documentation
│   │   │   └── install-windows-11.md
│   │   └── tickets/                # Simulated support tickets with resolutions
│   │       └── TKT-001.md
│   ├── 02-cli-and-gui-tools/
│   ├── 03-windows-security/
│   ├── 04-networking/
│   ├── 05-active-directory/
│   ├── 06-asset-management/
│   ├── 07-software-deployment/
│   ├── 08-office-365/
│   └── 09-azure/
```

Each section folder follows the same pattern:

- **`skills/`** — step-by-step documentation of the technical skill as performed in the lab
- **`tickets/`** — a realistic user request that exercises that skill, with diagnosis and resolution steps recorded
- **`README.md`** — section overview, skills covered, and tickets raised

Skill docs and ticket docs cross-reference each other.

---

## Ticketing System

All tickets are raised and resolved in one of the three ticketing systems. The `<ticketing-service>-setup.md` file covers how the environment was configured — groups, ticket categories, priorities, and status workflow.


---

## Tools & Environment

- **Ticketing:** Freshdesk, ServiceNow, Jira Service Management
- **Virtualisation:** VirtualBox
- **OS:** Windows 11, Windows Server 2022
- **Directory:** Active Directory (lab domain `lab.local`)
- **Cloud:** Microsoft 365 Developer Tenant, Azure free tier

---

## License

MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
