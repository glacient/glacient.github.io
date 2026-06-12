---
title: Spaces
eyebrow: Spaces
summary: Share curated workflows with teammates without giving them edit rights.
permalink: /spaces/
---

Most people who use Glacient don't author workflows. They want a curated view of the ones someone else built. **Spaces** are how a power user packages a workflow for a team and lets them follow it without the risk of breaking it.

## The model

A Space has:

- An **owner**: the user who created the Space.
- **Members**: users who joined through a share code.
- **Attached workflows**: workflows the owner has exposed inside the Space.

Members see attached workflows as **read-only** canvases. They can pan, zoom, inspect each node, and read every threshold, but they can't move nodes, change thresholds, or delete anything. The owner edits the workflow in their own canvas and the Space picks up the changes.

## Roles

There are exactly two roles.

| Role | What they can do |
|---|---|
| Owner | Create the Space, generate a join code, approve or reject join requests, attach and detach workflows, remove members, delete the Space. |
| Member | View the Space, view attached workflows in read-only mode, leave the Space. |

There is no admin/editor/viewer tier on purpose. If you need to share editing rights, share the workflow itself, not a Space.

## Joining a Space

Spaces are discovered by **share link or code only**. There is no directory and no email invite. The owner sends you a link like:

```
/spaces/join/<code>
```

When you open it, you submit a join request. The owner sees it in their pending list, approves or rejects, and on approval you become a member. Until approval, the Space doesn't appear in your sidebar.

## Constraints

A few small but important rules:

- An owner cannot self-request membership in their own Space.
- A workflow attached to a Space cannot be archived or deleted by the owner without detaching it first. The canvas surfaces a notice when you hit this state.
- Removing a member detaches them immediately. Re-adding them requires a new join request.

## State

Spaces are either **Active** or **Archived**. Archived Spaces don't appear in members' navigation. Active Spaces appear next to the owner's workflows in their sidebar and in members' sidebars.

## What's next

- [Sharing workflows](/spaces/sharing/): how attached workflows look to members and how attachment works in practice.
- [Workflows](/concepts/workflows/): the underlying model.
