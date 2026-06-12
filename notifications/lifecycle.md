---
title: Alert lifecycle
eyebrow: Notifications
summary: How a workflow evaluates, fires, cools down, and re-arms.
permalink: /notifications/lifecycle/
---

This page is the precise version of "what happens when my workflow runs." If you've ever wondered why you didn't get a second notification, this is the model to read.

## Evaluation

While a workflow is **Active**, Glacient evaluates it on every tick. The triggers pull fresh values, the conditions compare them, and the terminal condition resolves to a boolean.

If the boolean is **false**, nothing else happens this tick.

If the boolean is **true**, Glacient looks at the action's cooldown state next.

## Cooldown

Each condition has a per-condition cooldown clock. After a successful fire, the clock starts at **12 hours**. While the clock is running, the same condition cannot fire its action again, even if the metric stays past the threshold.

The cooldown is **per condition**, not per workflow. A workflow with three conditions (say, APY, liquidity, and utilization) can fire three separate alerts in the same tick, and each of the three then starts its own clock independently.

## Delivery

When a fire passes the cooldown check, the action runs. For Telegram, that means a message is sent to the connected account. The message contains:

- The metric, operator, and threshold that fired.
- The current value at the moment of the fire.
- The collection (vault, market, position, event) along with chain and address.
- A link back to the workflow in the app.

Delivery latency is small. Expect the alert to land within seconds of the metric crossing your threshold.

## Re-arm

Once the cooldown expires, the condition is **re-armed**. The next tick that evaluates true will fire again.

This means: a condition like **Utilization Rate** above 95% will fire when utilization first crosses 95%, then go silent for 12 hours, then fire again 12 hours later if utilization is still above 95%. If you want a single notification per crossing rather than every 12 hours while the metric stays high, use `crosses_above` instead of `above`. See [Operators](/reference/operators/).

## State interaction

Cooldowns are scoped to the saved workflow. Pausing and unpausing a workflow does not reset cooldowns. Editing and re-saving a workflow creates a new version, and its cooldown clocks start fresh.

| Action | Effect on cooldown |
|---|---|
| Workflow paused | Cooldown clock continues, no evaluation happens |
| Workflow resumed | Resumes evaluation against existing clock |
| Workflow edited and saved | New version; cooldown clocks reset |
| Workflow archived | Cooldown clocks frozen until restore |

## What you'll see in practice

- A short flurry of "wait, why no notification" the first time a metric hangs near a threshold. It's the cooldown, not a bug.
- Cleaner inboxes than per-tick alerts would give you.
- A predictable cadence when something is genuinely stuck above or below your threshold for a long time.
