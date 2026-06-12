---
title: Saving and running
eyebrow: Building workflows
summary: What happens when you click Save, and how a workflow moves between active, paused, and archived.
permalink: /canvas/lifecycle/
---

The canvas is the editor. The **saved workflow** is what runs. This page covers the boundary between the two.

## Saving

When you click **Save**, Glacient persists the canvas as a workflow with three sections:

- **Collections.** Resolved assets keyed by `{address, chainId}`. For Aave specifically, `chain_id` is preserved per-asset because the same symbol can exist on multiple chains.
- **Transformers.** The metric and condition graph that turns collection data into a boolean.
- **Actions.** What runs when the boolean is true.

The save call is rejected if any collection is empty (no resolved assets), if a condition has no threshold, or if an action has no channels selected. The toolbar disables **Save** in those states so you can see the problem before submitting.

## States

A saved workflow is always in one of four states. State changes go through a single backend endpoint so the constraints are uniform.

| State | Evaluation | Visible in Workflows | Notes |
|---|---|---|---|
| **Draft** | No | Only while open in the editor | Unsaved canvas changes |
| **Active** | Yes | Yes | Alerts can fire |
| **Paused** | No | Yes (greyed) | Useful while tuning thresholds |
| **Archived** | No | Hidden by default | Restorable from the archive view |

Transitions between Active, Paused, and Archived go through the **Update Workflow Status** flow. The canvas doesn't write these directly anymore; the unified path is what enforces the constraints below.

## Constraints on archive and delete

You can't archive or delete a workflow that another member depends on through a [Space](/spaces/). If a workflow is attached to a Space, the canvas surfaces a notice and you'll need to either detach it from the Space first or remove the Space.

These constraints live on the backend, so they apply identically whether you triggered the action from the canvas, the workflow list, or the Space management UI.

## Editing an active workflow

Editing a live workflow doesn't pause it. As soon as you click **Save**, the new version takes over from the next evaluation tick. If you want a graceful transition (for example, you're swapping operators or thresholds and want to suppress the old alert from firing during the swap), move the workflow to **Paused**, save, and move it back to **Active**.

## Evaluation cadence

Glacient evaluates active workflows continuously. The exact tick rate is an implementation detail (and a topic to ask about in [Support](https://www.glacient.ai/support) if your use case depends on a specific latency). For the metrics you'll use day-to-day, expect alerts within a few seconds of the metric crossing the threshold.

## Cooldown vs. state

A cooldown is per-condition, not per-workflow. Pausing a workflow stops evaluation entirely; cooldowns affect a single condition that has recently fired. See [Alert lifecycle](/notifications/lifecycle/) for the difference in detail.
