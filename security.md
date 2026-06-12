---
title: Security model
eyebrow: Security
summary: The full picture of what Glacient touches, what it stores, and what it can't reach.
permalink: /security/
---

Glacient's security posture rests on one design choice: the platform is non-custodial. Everything else follows from that.

## What we touch

| Surface | Access |
|---|---|
| Public on-chain data | Read |
| Public protocol APIs (Morpho, Aave, Hyperliquid, Polymarket) | Read |
| Your alert configuration | Read/Write (stored in our database) |
| Your Telegram identity | Sent to (one-way) |
| Your wallet | Read public state only (see below) |
| Your private keys | Never |
| Your funds | Never |

## Wallet interactions

There are exactly two reasons Glacient asks for a wallet.

**Sign-In with Ethereum.** When you choose to authenticate with a wallet, your wallet signs a SIWE message. The signature is gasless, proves you control the address, and grants no authority to move funds or approve tokens. It's a login, not a transaction.

**Read-only discovery.** When you use **My Investments** to find vaults you've deposited into, Glacient reads public on-chain deposit positions tied to the connected address. There's no signature involved. No prompt to approve a transaction. No permission granted beyond what any block explorer has.

In both cases, the wallet retains complete control. The flow never requires nor accepts a transaction-signing request.

## What we store

Stored in Glacient's database:

- Account identifier and your chosen authentication method.
- Email address and hashed password (if you signed up with email).
- Workflow definitions: collections, conditions, actions, thresholds.
- Connected Telegram identity (so we can send alerts).
- Connected wallet addresses (so we can show My Investments).

Not stored:

- Plaintext passwords.
- Private keys.
- Seed phrases.
- Anything that would let us act as you on-chain.

## Account safety

A few habits make the account itself harder to take over.

- Use unique, strong passwords if you signed up with email. Use a manager.
- Enable 2FA on your Google account if you signed up with Google.
- For wallets holding meaningful value, use a hardware wallet for the SIWE login flow.
- Always verify the URL you're on is `glacient.ai` before connecting a wallet.

## Reporting

If you find a security issue, please report it at [glacient.ai/support](https://www.glacient.ai/support) under **Report Issue**. We respond as fast as we reasonably can. Please don't open a public GitHub issue for a security report.
