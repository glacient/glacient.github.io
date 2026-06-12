---
title: The canvas
eyebrow: Building workflows
summary: A visual editor for non-custodial DeFi workflows. Drag nodes, wire them up, save.
permalink: /canvas/
---

The canvas is where workflows live. Nodes on the left feed into nodes on the right; a workflow is just a graph of those nodes. Everything you do on the canvas is editable, undoable, and saved as a single workflow when you click **Save**.

## Opening the canvas

- **Workflows → New workflow** opens a blank canvas.
- **Workflows → [Existing workflow] → Edit** loads the existing graph for editing.
- **Workflows → Templates** lets you fork from a pre-built workflow.

## The toolbar

Across the top of the canvas:

| Control | What it does |
|---|---|
| **Add Collection** | Drop a new collection node (Morpho vault, Aave market, etc.). |
| **Add Condition** | Drop a metric filter or boolean combinator. |
| **Add Action** | Drop an Alert node. |
| **AI prompt** | Open the natural-language builder. |
| **Templates** | Browse curated starter workflows. |
| **Save** | Persist the canvas as a saved workflow. |

The toolbar is gated by the same constraints as the backend. For example, **Save** stays disabled until every collection has resolved at least one underlying asset.

## Connections

Wire nodes together by dragging from the output port of one node to the input port of the next. The general flow is:

```
Collection → Trigger → Condition → Action
```

Connections enforce shape: you can't wire an Aave market directly into a Morpho metric, and you can't wire two actions to each other. Invalid drops are rejected with a hint about why.

## Editing a node

Click a node to open its side panel.

- **Collections** expose the asset picker, chain selector, and asset list.
- **Conditions** expose operator, threshold, and (where relevant) window size.
- **Actions** expose channel selection and template.

Changes apply live. Save when you're done.

## Read-only mode

When you're viewing a workflow through a [Space](/spaces/), the canvas opens in read-only mode. The graph is fully interactive (pan, zoom, inspect nodes), but every gesture that would mutate state is disabled. Space members get the visibility of the workflow without the ability to break it.

## What's next

- [Saving and running](/canvas/lifecycle/): what happens when you click Save.
- [Workflows](/concepts/workflows/): the model behind what you're editing.
