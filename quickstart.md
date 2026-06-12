---
title: Quickstart
eyebrow: Get started
summary: Sign in, connect Telegram, and ship your first alert in about five minutes.
permalink: /quickstart/
---

By the end of this guide you'll have a live alert watching a market you care about, with notifications arriving on Telegram. No code, no keys, no transactions.

## 1. Sign in

Open the [Glacient app](https://www.glacient.ai) and click **Login**. You can use any of three methods:

- **Google.** Fastest path, no email verification, account created on the spot.
- **Wallet.** Connect MetaMask, Coinbase Wallet, Rainbow, or any WalletConnect wallet. You'll be asked to sign a Sign-In with Ethereum (SIWE) message. The signature is gasless and grants no spending authority.
- **Email and password.** Standard signup with email verification.

You can link multiple methods to the same account later. See [Sign in](/sign-in/) for the full reference.

## 2. Connect Telegram

Alerts are delivered over Telegram today. To receive them:

1. Click the **gear icon** in the top nav to open **Account Configuration**.
2. In the **Telegram** section, click **Connect Telegram**.
3. Open the link to the Glacient bot and press **Start**.
4. Return to Glacient. The Telegram section shows **Connected**.

If anything goes wrong, the [Telegram setup guide](/notifications/telegram/) covers the most common pitfalls.

## 3. Add the first thing to watch

The fastest path to a working alert is to open the canvas and describe what you want.

1. Go to **Workflows → New workflow**.
2. In the AI prompt box, type something like:

   > Alert me when the 6-hour supply APY on Steakhouse PYUSD drops below 4%.

3. Glacient resolves the vault by name, drops a Morpho Vault collection on the canvas, wires it into a metric condition, and attaches a Telegram alert action.
4. Review the nodes. If the resolver picked the wrong vault, click the node and pick the right one from the dropdown.
5. Click **Save**.

Prefer to click? See [The canvas](/canvas/) for the manual flow.

## 4. Wait for a signal

Glacient evaluates your workflow continuously. The instant the condition fires, the Telegram alert lands. After it triggers, the same condition enters a **12-hour cooldown** so you don't get the same notification repeatedly while the metric hovers around your threshold. See [Alert lifecycle](/notifications/lifecycle/) for the full state machine.

## What's next

- [Workflows](/concepts/workflows/): the model behind what you just built.
- [Protocols](/protocols/morpho/): what's available to watch on each supported venue.
- [Spaces](/spaces/): share a curated workflow with teammates without giving them edit rights.
