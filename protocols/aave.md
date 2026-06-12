---
title: Aave
eyebrow: Protocols
summary: Watch Aave V3 reserve assets on Ethereum and Base.
permalink: /protocols/aave/
---

Glacient supports Aave V3 reserve assets as a first-class collection type. Aave markets are referred to by **token symbol** plus an optional chain, and Glacient resolves the symbol to the protocol's full market data automatically.

## Coverage

| Surface | Chains | Versions |
|---|---|---|
| Reserve assets | Ethereum, Base | Aave V3 |

A non-exhaustive list of supported assets:

- Stablecoins: `USDC`, `USDT`, `DAI`, `USDS`, `USDE`, `PYUSD`
- Wrapped majors: `WETH`, `WBTC`
- Others: the resolver covers anything Aave lists; ask for the symbol you want.

## Referring to a market

Aave collections take token symbols as inputs:

```json
{ "type": "aave-markets", "markets": ["PYUSD", "USDC"], "chainId": 1 }
```

If `chainId` is omitted, Ethereum (chain 1) is assumed. To watch the same symbol on Base, name the chain explicitly in the prompt: "Aave USDC on Base."

Unlike Morpho, Glacient stores Aave collections keyed by `{address, chainId}` because the same symbol can exist with different reserves on different chains. The chain ID survives the round-trip when the workflow is saved.

## Supply metrics

| Metric | Description |
|---|---|
| 6H Supply APY (Native) | 6-hour average native supply APY |
| Real-Time Supply APY | Current native supply APY (excludes rewards). Spiky |
| Merkl Supply Reward APY | Current Merkl reward APY for supplying |
| Net Supply APY | Native APY plus Merkl supply rewards |
| Remaining Supply Capacity | Headroom under the supply cap |
| Total Supply | Total amount supplied to the market |

## Borrow metrics

| Metric | Description |
|---|---|
| 6H Borrow APY | 6-hour average native borrow APY |
| Real-Time Borrow APY | Current native borrow APY. Spiky |
| Merkl Borrow Reward APY | Current Merkl reward APY for borrowing |
| 6H Net Borrow APY | 6-hour average net borrow APY (native minus Merkl rewards) |
| Net Borrow APY | Current net borrow APY (native minus Merkl rewards). Spiky |
| Remaining Borrow Capacity | Headroom under the borrow cap |
| Total Borrow | Total amount borrowed from the market |
| Utilization Rate | Borrowed ÷ available borrow capacity |
| Borrow Cap % | Closeness to the absolute borrow cap |
| Liquidity | Total liquidity available in the market |

## Typical workflows

- **Yield watch.** `USDC` on Ethereum, **6H Supply APY (Native)** below 3.5% → Telegram alert.
- **Liquidity guard.** `USDT` on Ethereum, **Remaining Borrow Capacity** below 5,000,000 → Telegram alert. Useful for borrowers worried about running out of headroom before rolling.
- **Cap pressure.** `WETH` on Base, **Borrow Cap %** above 85% → Telegram alert. Catches markets approaching saturation before borrowing becomes unavailable.
- **Rate spike.** `WBTC` on Ethereum, **Real-Time Borrow APY** above 6% → Telegram alert.

See [Metrics catalog](/reference/metrics/) for the full list and [Chains](/reference/chains/) for chain coverage.
