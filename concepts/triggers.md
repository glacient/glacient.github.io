---
title: Triggers
eyebrow: Core concepts
summary: Triggers turn a collection into a stream of numbers that conditions can compare against.
permalink: /concepts/triggers/
---

A **trigger** is the metric you want to watch. On every evaluation tick, the trigger reads its parent collection and emits a value: an APY percentage, a liquidity figure in USD, a utilization rate, a position's unrealized PnL, and so on.

## Why triggers are separate from conditions

A condition fires when a number crosses a threshold. The number has to come from somewhere, and that's the trigger. Splitting the two means:

- You can watch multiple metrics on the same collection.
- You can compose conditions over the same metric (for example, `above 80%` and `below 40%` as two separate alerts).
- The same protocol metric is consistent across workflows.

## Available metrics

Triggers are protocol-aware. See the per-protocol pages for the full set:

- [Morpho metrics](/protocols/morpho/)
- [Aave metrics](/protocols/aave/)
- [Hyperliquid metrics](/protocols/hyperliquid/)
- [Polymarket metrics](/protocols/polymarket/)

A compact catalog is also kept at [Reference → Metrics](/reference/metrics/).

## Evaluation cadence

Glacient evaluates every active workflow continuously against live protocol data. Each trigger pulls the freshest snapshot it has cached. Different metrics have different freshness guarantees. For example, the **6-hour APY** is intentionally a smoothed window, while **current APY** is an instantaneous read. Use whichever you actually want to alert on. Mixing them in one workflow is fine.

## Multiple triggers per collection

Triggers attach to a collection, not the other way around. A single Morpho Vault collection might fan out to:

- a **6H Supply APY (Net)** trigger feeding a "yield dropped" alert,
- a **Liquidity** trigger feeding a "liquidity drained" alert,
- and a **Real-Time Net Supply APY** trigger feeding a "rate spike" alert.

This keeps the canvas readable and lets you reuse the same collection for several alert paths without duplicating it.
