---
title: Sharing workflows
eyebrow: Spaces
summary: Attach a workflow to a Space and members will see it as a read-only canvas.
permalink: /spaces/sharing/
---

This page covers what happens when an owner attaches a workflow to a Space and a member opens it.

## Attaching a workflow

From a Space you own:

1. Click **Attach workflow**.
2. Pick from your workflow list.
3. The workflow appears in the Space's panel with the name it had at attach time and a link to open it as a member would.

The workflow itself isn't copied. The Space holds a reference to it: a `{space_id, workflow_id}` pair plus a name snapshot for display purposes. Edits you make in your own canvas are reflected in the Space immediately.

## The member view

When a member opens an attached workflow, they get the canvas in **read-only mode**. Concretely:

- Pan and zoom are enabled.
- Clicking a node opens its side panel for inspection.
- Every form input is disabled.
- The toolbar's mutating buttons (Save, Add, Delete) are hidden.
- A subtle banner across the top of the canvas indicates the workflow is read-only.

This is the same `WorkflowCanvas` used for editing, gated by a single read-only flag. The behavior is identical to what an editor sees with the canvas locked.

## Detaching

Detaching removes the reference from the Space. The workflow itself is untouched: it stays in the owner's workflow list and continues evaluating. Members will no longer see it.

You'll need to detach a workflow before archiving or deleting it, since the backend rejects status changes on workflows that other members still depend on.

## What members can do without seeing the canvas

Even before opening the canvas, members of a Space see:

- The Space's name and description.
- The list of attached workflows.
- Each workflow's name snapshot, so the title stays stable even if the owner renames it later.

Alerts fire to the **owner's** notification channels, not the members'. Sharing the workflow is a visibility tool, not a notification fan-out. If members want their own alerts, they should build their own workflows.

## Owner workflow vs. member workflow

When you own a workflow, it lives in your **Workflows** view and you can edit it freely. When you're a member of a Space that includes that workflow, it appears in the Space's panel as a read-only view. The same workflow can absolutely show up in both places when you own it; they're two windows onto the same underlying object.
