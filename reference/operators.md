---
title: Operators
eyebrow: Reference
summary: Every operator a condition can use, and when to pick each one.
permalink: /reference/operators/
---

Operators are the comparison primitives in a condition. Pick the one that matches the question you're actually asking.

## Single-value operators

| Operator | Fires when | Use case |
|---|---|---|
| `above` | trigger value > threshold | "Tell me while utilization is high." Combines with the 12-hour cooldown for periodic reminders. |
| `below` | trigger value < threshold | "Tell me while remaining capacity is tight." |
| `equals` | trigger value ≈ threshold | Rarely useful; most metrics are floats. Has a small tolerance. |

## Crossing operators

| Operator | Fires when | Use case |
|---|---|---|
| `crosses_above` | prev tick ≤ threshold AND current tick > threshold | "Tell me **once** when something starts being high." |
| `crosses_below` | prev tick ≥ threshold AND current tick < threshold | "Tell me **once** when something drops below." |

Crossing operators are usually what you want for clean one-shot alerts. `above`/`below` are better when you want repeated reminders (subject to the cooldown) for as long as a condition holds.

## Change operators

| Operator | Fires when | Use case |
|---|---|---|
| `changes_by` | abs(current − prev) ≥ threshold | "Tell me when the metric moves by more than X." |
| `changes_pct` | abs(current − prev) / prev ≥ threshold | "Tell me when the metric moves by more than X percent." |

Change operators are the right pick for movement-sensitive metrics like Polymarket implied probability or Hyperliquid PnL.

## Boolean combinators

Two combinator nodes let you connect conditions on the canvas:

- **AND**: fires when both inputs are true on the same tick.
- **OR**: fires when either input is true.

These compose freely: you can wire AND into OR, OR into AND, and multiple conditions into a single combinator. The combinator's truth value is what controls the downstream action.

## Common mistakes

- **Using `above` when you mean `crosses_above`.** You'll get a periodic alert every 12 hours while the metric stays above. If you wanted "tell me once," `crosses_above` is what you want.
- **Setting `changes_by` too tightly.** Noise will trigger the alert constantly until it cools down. Look at a chart for the metric and pick a threshold above the typical tick-to-tick noise band.
- **Mixing percentage and absolute thresholds.** A condition on **Liquidity** above 10 means "above $10," not "above 10%." Metrics that compare as percentages are labelled as such on the canvas (e.g. **Utilization Rate**, **Borrow Cap %**) — enter the threshold as a percent.
