---
title: Self-custody
eyebrow: Core concepts
summary: What Glacient can and cannot do with your wallet.
permalink: /concepts/self-custody/
---

Glacient is fully **non-custodial**. The product is built on a single hard constraint: your keys, your assets, your call. Nothing in the system depends on Glacient being able to move funds, and there is no path inside the app to ask you to sign a transaction.

## What Glacient does

- Reads public on-chain data (vaults, markets, positions, prices).
- Reads protocol APIs (Morpho, Aave, Hyperliquid, Polymarket).
- Stores the workflows you define (thresholds, alert preferences).
- Sends notifications to your connected channels.

## What Glacient does not do

- Hold your funds.
- Custody your private keys.
- Sign transactions.
- Move tokens between wallets, vaults, or markets.
- Approve token allowances.
- Trade on your behalf.

## Wallet connections

There are two kinds of wallet interaction in the app, and they're handled differently.

### Sign-In with Ethereum (SIWE)

When you choose **Login with Wallet**, Glacient asks your wallet to sign a SIWE message. The signature:

- Is **gasless**: there's no transaction, no on-chain footprint.
- Proves **you control the address**.
- Grants **no authority** to move funds or approve tokens.

That's the entirety of authentication. There's no second prompt, no allowance request, no permit.

### My Investments discovery

The **My Investments** flow lets you connect a wallet to surface vaults you've already deposited into so you don't have to paste addresses. Glacient reads public deposit positions from the chain (the same information any block explorer would show) and lists them in the picker.

This is **read-only**. No signature is required, and no permission is granted beyond what the wallet exposes by default to dapps.

## Roadmap: non-custodial automation

When on-chain actions ship, they will run through self-custody signing solutions (hardware wallets, smart account modules, and similar) so the keys stay with you while Glacient handles the orchestration. The product roadmap is explicit about this on the [glacient.ai](https://www.glacient.ai) landing page: **automation without compromise**.

## In one sentence

If something in the app ever asks you to sign a transaction or approve a token allowance, **stop**. That isn't a flow Glacient ships today. Disconnect your wallet, close the tab, and report it to support.
