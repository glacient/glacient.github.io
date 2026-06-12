---
title: Glacient
eyebrow: Introduction
summary: Monitor on-chain markets, route signals into alerts, and automate non-custodial DeFi workflows, no code required.
permalink: /
---

Glacient is the automation layer for DeFi. You describe what you want to watch, the conditions that matter, and where to send the result. Glacient runs it on a schedule against live protocol data and notifies you the moment a signal fires.

Everything you build is **non-custodial**. Glacient never holds your funds, never holds your keys, and never signs transactions on your behalf. The only things it reads are public on-chain data and the alert preferences you save.

<ul class="cards">
  <li><a class="card" href="/quickstart/">
    <div class="card-title">Quickstart →</div>
    <div class="card-desc">Sign in, connect Telegram, and ship your first alert in under five minutes.</div>
  </a></li>
  <li><a class="card" href="/concepts/workflows/">
    <div class="card-title">Core concepts →</div>
    <div class="card-desc">How collections, triggers, conditions, and actions compose into a workflow.</div>
  </a></li>
  <li><a class="card" href="/canvas/">
    <div class="card-title">The canvas →</div>
    <div class="card-desc">Drag, connect, and save workflows visually, or describe them in plain English.</div>
  </a></li>
  <li><a class="card" href="/protocols/morpho/">
    <div class="card-title">Protocol guides →</div>
    <div class="card-desc">Reference for Morpho, Aave, Hyperliquid, and Polymarket integrations.</div>
  </a></li>
</ul>

## What you can build

- **Yield watch.** Alert when the 6-hour supply APY on a Morpho vault drops below your floor.
- **Liquidity guards.** Notify yourself when remaining borrow capacity on an Aave market falls under a threshold.
- **Position health.** Monitor an open Hyperliquid perp and signal when the unrealized PnL or liquidation distance crosses a line you set.
- **Event surfaces.** Watch a Polymarket market's price or volume and forward changes to Telegram.
- **Allocation drift.** Track vault curator allocations across markets and get a ping the moment composition shifts.

## How Glacient is organized

Every workflow has the same shape:

1. **Collections**: the markets, vaults, positions, or events you want Glacient to watch.
2. **Triggers and conditions**: the metrics, thresholds, and operators that decide when a signal fires.
3. **Actions**: what happens when it does. Today: alerts over Telegram, with more notification channels and on-chain execution arriving on the roadmap.

You can build a workflow by describing it in natural language or by [dragging nodes on the canvas](/canvas/). Both produce the same saved workflow, and both can be edited freely after.

## Read next

- [Quickstart](/quickstart/): sign in, connect, alert.
- [Workflows](/concepts/workflows/): the underlying model.
- [Self-custody](/concepts/self-custody/): what Glacient can and cannot do with your wallet.
