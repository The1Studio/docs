---
title: Module status cascade
description: Completing or cancelling a Module can also move every work item in it — and each item's sub-items — to the matching state, behind a confirmation dialog that never cascades by default.
---

# Module status cascade

When you move a Module to **Completed** or **Cancelled**, you can also move every work item in that Module — and each work item's sub-items — to the matching state. Completing a Module completes its live work items; cancelling a Module cancels them.

The cascade is always a deliberate choice. A plain status change never cascades: Plane asks first, and the confirmation dialog is set up so that pressing **Enter** or clicking the default action leaves the work items untouched.

This applies to both directions of the cascade:

- A work item already **Done** is never re-opened or cancelled.
- A work item already **Cancelled** is never completed.

## When the dialog appears

The confirmation dialog only appears when there is something to change. A Module with no live work items changes status directly, with no prompt.

## The dialog's default keeps work items safe

The dialog's default button is **Only change this module**, and it holds focus. Pressing **Enter** at any point changes the Module's status and nothing else — cascading must be selected deliberately as the second choice.

The dialog leads with a summary of what will change:

- **Will change** — how many work items will be moved to the matching state.
- **Already done** — how many are already in a terminal state and will be left as they are.
- **Cannot change** — how many are out of reach (see below).

Below the summary is the full checkbox list of the work items the cascade would change. When the list is long, it is collapsed behind a disclosure; open it to review or edit the selection. You can untick individual items to exclude them from the cascade.

## Items you cannot change

A work item you cannot access, or one in a project that has no state matching the target status, is listed **disabled with the reason** rather than hidden. Disabled items are never changed by the cascade.

## Over 100 items: the cascade is refused, not truncated

The cascade is capped at 100 work items. Over that cap the cascade is **refused outright** — the preview is empty and applying writes nothing. The dialog says the Module is too large to cascade, its only action is **Only change this module**, and the Module's status still changes as you asked. Nothing is quietly truncated to fit.

## Cascade behavior on sub-items

A work item already in a terminal state stops the cascade at that branch of the tree. Nothing beneath it is changed — a live sub-item under a cancelled parent stays live instead of being swept along. The same holds for the existing per-work-item cascade, not just the new Module-level one.

## API endpoints

The Module cascade is exposed as two endpoints:

```
GET  .../modules/{module_id}/cascade-preview/?status=<completed|cancelled>
POST .../modules/{module_id}/cascade-apply/    body {status, item_ids}
```

`cascade-preview` returns the items the cascade would change for a given Module status; `cascade-apply` writes the change for the item IDs you confirm. See the [developer-docs API reference](https://developers.plane.so/api-reference/introduction) for the request and response shapes.
