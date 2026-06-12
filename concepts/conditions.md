---
title: Conditions
eyebrow: Core concepts
summary: Conditions compare a trigger's output against a threshold and decide whether an action runs.
permalink: /concepts/conditions/
---

A **condition** is the gate between a trigger and an action. It takes the value the trigger emits, compares it against a threshold you set, and resolves to either `true` (run the downstream action) or `false` (do nothing this tick).

## The shape of a condition

Every condition has three parts:

- **Source**: the trigger feeding it.
- **Operator**: how to compare. See [Reference → Operators](/reference/operators/) for the full list.
- **Threshold**: the value to compare against.

For example:

> When the **6-hour supply APY** of `Steakhouse PYUSD` is **below** `4`, alert me.

## Operator semantics

| Operator | Fires when |
|---|---|
| `above` | trigger value is strictly greater than threshold |
| `below` | trigger value is strictly less than threshold |
| `crosses_above` | value was at or below threshold on the previous tick and is now above |
| `crosses_below` | value was at or above threshold on the previous tick and is now below |
| `equals` | value matches threshold within a small tolerance |
| `changes_by` | value moved by more than threshold (absolute or percentage, depending on metric) |

`crosses_*` is usually what you want for "tell me once when it happens." `above`/`below` is right for "tell me while it is in this state" (combined with the cooldown, see below).

## Combining conditions

You can join conditions with `AND` and `OR` on the canvas. The terminal condition's truth value is what controls the action.

- **AND.** Useful when you want both a metric and a guard. "Alert me when APY drops below 4% **and** liquidity is still above $10M."
- **OR.** Useful as a single alert covering several reasons to react. "Alert me when utilization is above 95% **or** remaining borrow capacity is below $1M."

## Cooldowns

Once a condition fires and its action runs, Glacient applies a **12-hour cooldown** to that specific condition. Re-evaluation continues, but the same alert won't trigger again within the window even if the metric stays past the threshold.

This is a deliberate tradeoff: it protects you from alert fatigue when a metric oscillates around your threshold. If you need a different behavior (for example, "ping me every hour while liquidation distance is below 2%"), that requires a workflow change today, not a per-condition cooldown override.

See [Alert lifecycle](/notifications/lifecycle/) for the full state machine.
