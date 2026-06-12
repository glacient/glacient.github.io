---
title: Actions
eyebrow: Core concepts
summary: Actions are what runs when a workflow fires.
permalink: /concepts/actions/
---

An **action** is the side effect at the end of a workflow. Today, Glacient supports notification actions, primarily Telegram. The action model is designed so that on-chain execution and additional channels can be added without changing the rest of the workflow shape.

## Alert action

The default action is **Alert**. It sends a notification to the channels configured on your account when its upstream condition fires.

The alert payload includes:

- The triggering condition (metric, operator, threshold).
- The current value that crossed the threshold.
- The collection it came from (vault, market, position) along with chain and address.
- A short, human-readable summary.

## Channels

| Channel | Status |
|---|---|
| Telegram | Available on all plans. See [Telegram](/notifications/telegram/). |
| Email | Roadmap. |
| Webhook | Roadmap (Enterprise). |
| Slack | Roadmap. |
| SMS | Roadmap. |

A single Alert action can be routed to multiple channels once they're connected. You don't need a separate action per channel.

## Templates

The Alert action uses a **Basic Alert** template by default. The template controls how the payload is formatted into the message body: protocol context up top, metric and threshold in the middle, link back to the workflow at the bottom.

## On-chain actions

Glacient is built to evolve from "Monitor and Alert" to "Monitor, Alert, and **Automate**." On-chain action support (moving deposits between vaults, adjusting LTV, closing perp positions) will run through self-custody signing solutions so your assets never leave your wallet. See the [Glacient landing page](https://www.glacient.ai) for the roadmap.

Until then: actions are observational. Glacient can tell you what's happening; you decide what to do about it.
