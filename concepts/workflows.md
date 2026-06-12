---
title: Workflows
eyebrow: Core concepts
summary: A workflow ties what to watch to what to do.
permalink: /concepts/workflows/
---

A **workflow** is the unit of work in Glacient. It pairs a set of things to watch with the conditions that decide when a signal fires and the action that should run when one does. Workflows are non-custodial, idempotent, and editable at any time.

## Anatomy

Every workflow is built from four kinds of nodes:

| Node | Role | Example |
|---|---|---|
| **Collection** | The set of markets, vaults, positions, or events to watch. | A Morpho Vaults collection containing `Steakhouse PYUSD` on Ethereum. |
| **Trigger** | A metric on a collection that emits a number on every evaluation tick. | **6H Supply APY (Net)** on the vault. |
| **Condition** | An operator that compares trigger output against a threshold. | `below 4%` |
| **Action** | What runs when the condition is true. | Send a Telegram alert. |

The nodes are wired by **connections** that flow left to right: collection → trigger → condition → action. Glacient evaluates the chain on every tick. When the terminal condition is true and the action's cooldown has elapsed, the action fires.

## Composition

Workflows are graphs, not lists. Some practical consequences:

- A single collection can feed multiple triggers. Watch APY and liquidity on the same vault from one node.
- Multiple triggers can fan into the same action. One Telegram alert covers two conditions.
- Conditions can be combined with logical operators (`AND`, `OR`) so a fire requires several metrics to agree.
- You can mix protocols in one workflow. A condition on an Aave market plus a condition on a Morpho vault can both feed the same alert.

## Lifecycle

When you save a workflow, Glacient persists it as a strongly typed structure with Collections, Transformers, and Actions, keyed by `{address, chainId}`. The saved workflow is what the backend evaluates; the canvas is what you edit.

| State | Meaning |
|---|---|
| **Draft** | Nodes exist on the canvas but have not been saved. No evaluation happens. |
| **Active** | Saved and evaluated continuously. Alerts can fire. |
| **Paused** | Saved but not evaluated. Useful to silence noisy workflows while you tune. |
| **Archived** | Hidden from the Workflows list and not evaluated. Restorable. |

State transitions go through the same backend constraint that protects shared workflows in [Spaces](/spaces/). For example, you can't archive a workflow that another member depends on without detaching it first.

## Where workflows are used

- **Personal workflows** show up on the **Workflows** page.
- **Shared workflows** are attached to a [Space](/spaces/) and rendered read-only to members.

For the visual and AI-prompted editing flows, see [The canvas](/canvas/).
