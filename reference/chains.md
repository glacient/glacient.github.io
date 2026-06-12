---
title: Chains
eyebrow: Reference
summary: Which chains Glacient supports per protocol, today and on the roadmap.
permalink: /reference/chains/
---

This page is the canonical answer for "do you support X on chain Y?" If a row is missing, the answer is "not today."

## Today

| Protocol | Ethereum | Base | Arbitrum | HyperEVM | Solana |
|---|:---:|:---:|:---:|:---:|:---:|
| Morpho vaults | ✓ | ✓ | ✓ | ✓ |   |
| Morpho markets | ✓ | ✓ | ✓ | ✓ |   |
| Aave V3 reserves | ✓ | ✓ |   |   |   |
| Hyperliquid | n/a | n/a | n/a | n/a | n/a |
| Polymarket | n/a | n/a | n/a | n/a | n/a |

**Hyperliquid** and **Polymarket** are operationally chain-agnostic from a Glacient user's perspective; the chain that hosts them doesn't change how you set up the collection. They're listed here for completeness.

## Roadmap

These are publicly announced but not yet available:

- **Solana**. Morpho support.
- **Arbitrum**. Aave V3 coverage.
- **Optimism**. Aave V3 coverage.
- **Additional protocols**. Euler, Kamino.

For status updates, check the **Future Roadmap** tab in the Glacient app or [glacient.ai](https://www.glacient.ai).

## Chain IDs in the API

For the integrations that store collections keyed by chain (currently Aave), the `chainId` field uses standard EVM chain IDs:

| Chain | ID |
|---|---|
| Ethereum | 1 |
| Base | 8453 |
| Arbitrum | 42161 |
| Optimism | 10 |

If you're using the AI prompt, you don't need to know these; naming the chain in plain English ("on Base", "on Arbitrum") is enough.
