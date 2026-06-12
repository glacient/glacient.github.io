---
title: Polymarket
eyebrow: Protocols
summary: Watch Polymarket markets and events as a first-class collection.
permalink: /protocols/polymarket/
---

Glacient treats Polymarket markets and events as monitored collections, the same model used for DeFi venues, applied to prediction markets. You pick the markets, attach metric conditions, and route signals into alerts.

## Coverage

| Surface | Notes |
|---|---|
| Markets | Individual market outcomes with price, volume, and depth metrics. |
| Events | Aggregated views combining the markets under a single event. |

Glacient uses the keyset-paginated `/markets/keyset` and `/events/keyset` endpoints to list and search. (The legacy offset-based endpoints were deprecated by Polymarket in 2026.)

## Referring to markets

Markets are pickable through the collection node's search panel. Once selected, they're stored in the workflow by their canonical Polymarket identifier so re-resolution at evaluation time is stable.

## Metrics

Common metrics available on Polymarket collections:

- **YES Outcome / NO Outcome**: implied probability of each side, derived from the current market price.
- **24h Volume**: total trading volume over the last 24 hours.
- **Liquidity**: total liquidity available in the market.
- **Spread**: bid-ask spread. Smaller = more liquid.

The full set is surfaced on the collection node. The reference list lives in [Metrics catalog](/reference/metrics/).

## Typical workflows

- **YES probability cross.** Market on a political outcome, **YES Outcome** above 60% → Telegram alert.
- **Volume surge.** Event collection, **24h Volume** above 1,000,000 → Telegram alert.
- **Spread tightening.** Market, **Spread** below 0.5% → Telegram alert. Signals the market is becoming more liquid.

## When the integration is most useful

Polymarket monitoring shines when you want to react to a market reflecting new information faster than your news sources will. Pair a tight `changes_by` threshold with the [12-hour cooldown](/notifications/lifecycle/) and you'll get a clean ping when the market starts moving and silence afterward.
