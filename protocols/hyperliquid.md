---
title: Hyperliquid
eyebrow: Protocols
summary: Watch perp market data and surface a wallet's active positions in your workflow.
permalink: /protocols/hyperliquid/
---

Glacient integrates with Hyperliquid through two collection types: **Perp Markets** (market-level data, no wallet needed) and **User Positions** (a wallet's active perps). Both attach to the same metric-and-condition machinery used everywhere else in Glacient.

## What you can monitor

**Perp Markets** are scoped by coin (BTC, ETH, HYPE, …). No wallet required. Useful for funding-rate hunting, premium signals, OI spikes, and price triggers on the underlying.

**User Positions** are scoped to a wallet. Glacient previews the active perps in the collection panel and lets you pick which ones feed the workflow. Useful for PnL alerts, liquidation guards, and size-change detection.

For the full list of metric IDs in each, see the [Metrics catalog](/reference/metrics/).

## Adding Perp Markets

1. Add a Hyperliquid Perp Markets collection.
2. Enter the coin symbols you want to track. Symbols are case-sensitive and Hyperliquid-specific (e.g. `BTC`, `ETH`, `HYPE`, `kPEPE`).
3. Attach the metric and condition.

## Adding a Hyperliquid wallet

1. Add a Hyperliquid User Positions collection.
2. Paste the wallet address.
3. Glacient previews the active perp positions.
4. Pick the positions to include.

The flow is read-only. Glacient never asks for keys, signing authority, or anything that would let it manage the position. It pulls the same information available from Hyperliquid's public APIs.

## Typical workflows

- **Funding-rate signal.** Perp Markets on `HYPE`, **Funding Rate (1H)** above 0.01% → Telegram alert. Catch funding spikes.
- **PnL alert.** User Positions on `ETH`, **Return on Equity** below -10% → Telegram alert. Fires when the position is 10% underwater on margin.
- **Liquidation guard.** User Positions on `BTC`, **Liquidation Price** above your safety threshold → Telegram alert. Wakes you before a margin call.
- **Size change.** User Positions on any coin, alert when **Position Size** crosses a threshold. Useful for shared accounts to spot unexpected modifications.

## Self-custody note

Monitoring a Hyperliquid wallet does **not** grant Glacient any authority over the account. Glacient does not co-sign trades and does not close positions. If you want to react to a Glacient alert, you'll act in Hyperliquid directly. See [Self-custody](/concepts/self-custody/).
