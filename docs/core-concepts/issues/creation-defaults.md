---
title: Work item creation defaults
description: New work items are assigned to you and due today unless you say otherwise — and how to create one that is deliberately unassigned or has no due date.
---

# Work Item Creation Defaults

## Overview

When you create a work item without choosing an assignee or a due date, Plane fills both in for you:

- **Assignee** — you, the person creating it.
- **Due date** — today.

The point is that a new work item starts out owned and dated rather than drifting unassigned in a backlog nobody is watching. Both values are visible before you save, and both can be changed or removed.

This applies everywhere a work item is created: the **Add work item** dialog, the inline **+ New work item** row in the List, Board, Calendar and Spreadsheet views, sub-work items, and epics.

## Changing or removing the defaults

The assignee chip and the due-date pill are prefilled in the create dialog, not locked. Set them to whatever you want before saving.

To create a work item that is **deliberately unassigned**, clear the assignee chip. To create one with **no due date**, clear the due-date pill. Plane treats a cleared field as a real choice and saves it empty — it does not put the default back.

::: tip
Clearing a field is the supported way to opt out, not a workaround. If you clear the due date and save, the work item has no due date; nothing re-adds one later.
:::

## When your project has a default assignee

If your project has a **default assignee** configured in project settings, that person is assigned instead of you. The creator is only the fallback for projects that have not set one, so configuring a default assignee keeps working exactly as it did before.

If neither applies — for example you are creating the item in a project you are not a member of — the work item is created unassigned rather than assigned to someone who cannot see it.

## Which "today" you get

The due date is **today in your own timezone**, taken from the timezone in your Plane profile, not the server's. If you are working at UTC+7 and create a work item at 6 in the morning, you get today's date as you see it, not yesterday's.

One exception: if you set a **start date in the future** and leave the due date empty, the due date becomes that start date rather than today. A work item cannot be given a due date that falls before its own start date.

## Where the defaults do not apply

- **Editing an existing work item.** The defaults only ever run at creation. If you clear the due date on an existing work item, it stays cleared.
- **Intake.** Items submitted through a project's intake queue arrive with no assignee and no due date, so a triage queue still reflects what was actually submitted.

Sub-work items, epics and drafts do get the defaults — they are created the same way as any other work item.
