---
title: Telegram
eyebrow: Notifications
summary: Connect your Telegram account to receive Glacient alerts.
permalink: /notifications/telegram/
---

Telegram is the default notification channel for Glacient alerts. Setup is a two-step handshake with the Glacient bot, no API keys, no group setup.

## Connect Telegram

1. Click the **gear icon** in the top nav to open **Account Configuration**.
2. In the **Telegram** section, click **Connect Telegram**.
3. Open the bot link. Telegram launches the chat with the Glacient bot.
4. Press **Start** in the bot.
5. Return to Glacient. The Telegram section shows **Connected**.

That's it. Any workflow with a Notify action set to Telegram will route to the connected account.

If a workflow's Notify action is set to Telegram but you haven't connected yet, the canvas will surface an "Open account settings" link that takes you to the same place.

## Bot commands

The Glacient bot accepts a small set of commands inside the chat:

| Command | What it does |
|---|---|
| `/start` | Initiates or repeats the connection handshake. |
| `/status` | Reports the connection state for the calling user. |
| `/help` | Prints a short help message. |

## Multiple connections

One Glacient account maps to one Telegram identity at a time. To switch accounts, disconnect from Account Configuration first, then run `/start` against the bot from the new account.

## Troubleshooting

**Connection didn't complete.**

1. Confirm you pressed **Start** in the bot chat. Closing the chat before pressing Start aborts the handshake.
2. Disconnect in Account Configuration, wait 30 seconds, and reconnect.
3. Try a different browser if you previously had Telegram Web open with stale credentials.

**Alerts aren't arriving.** Walk the checklist:

- Account Configuration shows Telegram as **Connected**.
- At least one workflow is **Active**.
- The workflow has at least one Notify action wired in with Telegram as the channel.
- The bot isn't muted or blocked in Telegram.
- The condition has actually crossed its threshold since the last 12-hour cooldown reset.

If everything looks right and alerts still aren't arriving, the [Alert lifecycle](/notifications/lifecycle/) page documents how state transitions interact with delivery.

## Roadmap

Email, Slack, SMS, and webhook channels are on the roadmap. Once available, they'll route through the same Alert action, no workflow changes required.
