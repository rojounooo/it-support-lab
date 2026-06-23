# Jira Service Management Setup

Jira Service Management is used for Sections 4–6 of this lab (Windows Networking, Active Directory & Group Policy, Asset Management). This document covers the initial configuration needed before raising tickets.

---

## Account Creation

1. Go to [atlassian.com/software/jira/service-management](https://www.atlassian.com/software/jira/service-management) and click **Get it free**
2. Sign up using a Google account to avoid being prompted for a company domain
3. When asked what you work in, select **IT Support**

---

## Creating the Project

Jira will prompt you to create a project on first login:

| Field | Value |
|-------|-------|
| **Template** | IT Service Management |
| **Name** | e.g. `IT Support Lab` |
| **Key** | Auto-generated from the project name — leave as is |
| **Team type** | IT |
| **Channel access** | Restricted |

Click **Create project** to finish setup.

---

## Raising a Ticket

1. Click **Create** in the top navigation bar
2. Select **IT Help** as the request type for general support tickets
3. Fill in the following fields:

| Field | Value |
|-------|-------|
| **Raise this request on behalf of** | The requester — your own account or a customer contact |
| **Summary** | Short description of the issue, e.g. `User cannot access mapped network drive` |
| **Description** | The full request as a user would submit it |
| **Attachment** | Add any relevant screenshots |

4. Click **Create** to open the ticket

---

## Working a Ticket

Once a ticket is open, move it through the following statuses as work progresses:

| Status | When to use |
|--------|-------------|
| **Open** | Ticket has been received, work not yet started |
| **In Progress** | Actively being investigated or resolved |
| **Resolved** | Issue fixed, ticket closed |

Change the status using the status button at the top of the ticket view.

---

## Comments

Two comment types are available on each ticket:

| Type | Visible to | Used for |
|------|-----------|----------|
| **Reply to customer** | Requester and agents | User-facing updates — e.g. confirming receipt, requesting more info, notifying resolution |
| **Internal comment** | Agents only | Investigation notes, resolution steps, technical detail not relevant to the end user |

In this lab, **resolution steps are added as an internal comment** and the **outcome is added as a reply to customer** before resolving the ticket — mirroring real support team workflow.

---

## Priority Guide

| Priority | When to use |
|----------|-------------|
| Low | Routine task, no urgency |
| Medium | User affected but has a workaround |
| High | User fully blocked, no workaround |
| Critical | System down, multiple users affected |
