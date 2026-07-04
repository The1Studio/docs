---
title: Workload estimates and sub-item rollups
description: Track estimated hours per work item and see totals, progress, and due dates automatically rolled up from sub-items.
---

# Workload Estimates

## Overview

Plane tracks **Estimated hours** on work items so teams can plan workload in hours. The Estimated hours field appears in the work item sidebar, the spreadsheet view's Estimated hours column, and as a pill on list and kanban cards. Estimated hours also feed the Workload matrix, which totals hours per person across a day, week, or month.

## Parent items roll up estimates from sub-items

When a work item has sub-items, Plane doesn't ask you to estimate the parent directly. Instead, the parent automatically shows a rolled-up summary computed from its sub-items:

- **Total estimated hours** — the sum of estimated hours across all sub-items, including sub-items of sub-items.
- **Progress** — the percentage of those hours that belong to completed sub-items.
- **Due date** — the latest due date found anywhere in the sub-item tree.

This rollup appears wherever the Estimated hours field is normally shown:

- **Issue sidebar** — the Estimated hours field shows a read-only summary, e.g. `Σ 10h · 60%`, instead of an editable input.
- **Spreadsheet view** — the Estimated hours column shows the same read-only summary for parent rows.
- **List and kanban views** — the estimated-hours pill on the work item card shows the summary.

Hover over the summary to see a tooltip with the number of sub-items included in the rollup and the rolled-up due date.

::: info
You can't type an estimate directly on a parent work item — the field becomes read-only as soon as it has sub-items. Enter estimates on the sub-items instead; the parent's total, progress, and due date update automatically. Trying to set an estimate on a parent through the API returns an error explaining that estimates belong on the sub-items instead.
:::

## How progress is calculated

Progress is the share of estimated hours that belong to sub-items in a completed state, not a simple count of finished sub-items:

```
progress % = (estimated hours of completed sub-items) ÷ (total estimated hours of all sub-items)
```

For example, if a parent has two sub-items — one with an 8-hour estimate that's marked done, and one with an 8-hour estimate that's still in progress — the parent shows 50% progress.

If none of a parent's sub-items have an estimate yet, the parent shows `—` instead of a percentage, since there's nothing to calculate a percentage from.

Cancelled sub-items are excluded from every part of the rollup — their hours don't count toward the total, and they don't affect progress or the due date.

## Workload matrix and sub-items

The Workload matrix counts sub-items only. A parent work item and its sub-items are never both counted, which avoids double-counting a parent's hours on top of the hours already tracked on its individual sub-items.

## Known limitations

- **Refresh after adding or removing sub-items.** If you add or remove a sub-item, refresh the page to see the parent's total, progress, and due date update.
- **Restricted guests see a partial total.** Guests whose project access is limited to part of a work item's sub-item tree see totals computed only from the sub-items they can access, not the full tree.
