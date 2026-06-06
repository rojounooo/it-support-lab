# Freshdesk Setup

Freshdesk is used for Sections 1–3 of this lab (OS Installations, CLI & GUI Tools, Windows Security Controls). This document covers the initial configuration needed before raising tickets.

---

## Account Creation

1. Go to [freshdesk.com](https://freshdesk.com) and click **Start for free**
2. When prompted for an email, **use a Google account** — signing up with a personal or university email will prompt Freshdesk to ask for a company domain, which adds friction. Signing in with Google bypasses this
3. Follow the on-screen prompts to complete registration
4. You will be assigned a subdomain in the format `yourname.freshdesk.com` — this is your helpdesk URL

---

## Rename the Helpdesk

1. Go to **Admin → Account → Helpdesk Settings**
2. Update the **Helpdesk Name** field to something appropriate, e.g. `IT Support Lab`
3. Save changes

This name appears in the portal UI and in screenshots, so it's worth setting before raising any tickets.

---

## Add a Contact

Contacts represent end users who raise tickets. Creating a fake contact simulates tickets being submitted by a real user rather than an admin, which adds realism to the workflow.

1. Go to **Contacts** in the left sidebar
2. Click **New Contact**
3. Fill in the following fields:
   - **Name** — e.g. `Jane Smith`
   - **Email** — e.g. `jane.smith@corp-internal.com`
   - **Job Title** — e.g. `Sales Executive` (optional but adds context)
4. Click **Save**

You can create additional contacts for different ticket scenarios if needed, but one is enough to get started.

---

## Raise a Ticket

1. Go to **New Ticket** (top right, or via the **Tickets** tab)
2. Fill in the following fields:

| Field | Value |
|-------|-------|
| **Contact** | Select the contact you created (e.g. Jane Smith) |
| **Subject** | Short description of the issue, e.g. `Windows 11 installation required on new device` |
| **Type** | Select the most appropriate type from the dropdown |
| **Priority** | Set based on user impact (Low / Medium / High / Urgent) |
| **Description** | The full request as a user might submit it |

3. Click **Create** to open the ticket
4. Work through the resolution steps and add replies/notes as you go
5. Once resolved, change the ticket status to **Resolved**

---

## Priority Guide

| Priority | When to use |
|----------|-------------|
| Low | Routine task, no urgency — e.g. scheduled OS upgrade |
| Medium | User affected but has a workaround |
| High | User fully blocked, no workaround |
| Urgent | Critical system down, multiple users affected |