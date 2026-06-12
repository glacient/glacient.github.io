---
title: Metrics catalog
eyebrow: Reference
summary: Every metric Glacient currently surfaces, grouped by protocol.
permalink: /reference/metrics/
---

This is a single-page reference for the metrics you'll see on collection nodes and in saved workflows. Use it alongside the per-protocol guides for context and the [Operators](/reference/operators/) reference for how to compare them.

## Morpho vaults

| Metric | Type | Description |
|---|---|---|
| 6H Supply APY (Net) | Percentage | 6-hour average net supply APY, includes rewards and fees. More stable than real-time |
| 6H Supply APY (Native) | Percentage | 6-hour average native supply APY, excludes rewards |
| Real-Time Net Supply APY | Percentage | Current net supply APY (includes rewards, after fees). Spiky |
| Real-Time Native Supply APY | Percentage | Current native supply APY (excludes rewards). Spiky |
| Liquidity | USD | Total value locked in this vault |
| Token | Symbol | Vault's deposit token |

## Morpho markets

| Metric | Type | Description |
|---|---|---|
| 6H Supply APY (Net) | Percentage | 6-hour average net supply APY, includes rewards. More stable than real-time |
| 6H Supply APY (Native) | Percentage | 6-hour average native supply APY, excludes rewards |
| Real-Time Net Supply APY | Percentage | Current net supply APY (includes rewards). Spiky |
| Real-Time Native Supply APY | Percentage | Current native supply APY (excludes rewards). Spiky |
| Liquidity | USD | Total liquidity available in this market |
| Token | Symbol | Market's loan token |

## Aave markets

| Metric | Type | Description |
|---|---|---|
| 6H Supply APY (Native) | Percentage | 6-hour average native supply APY. More stable than real-time |
| Real-Time Supply APY | Percentage | Current native supply APY (excludes rewards). Spiky |
| Merkl Supply Reward APY | Percentage | Current Merkl reward APY for supplying |
| Net Supply APY | Percentage | Current native APY plus Merkl supply rewards |
| Remaining Supply Capacity | Asset units | Headroom under the supply cap |
| Remaining Borrow Capacity | Asset units | Headroom under the borrow cap |
| Liquidity | USD | Total liquidity available in this market |
| Total Supply | Asset units | Total amount supplied |
| Total Borrow | Asset units | Total amount borrowed |
| Utilization Rate | Percentage | Borrowed ÷ available borrow capacity |
| Borrow Cap % | Percentage | Closeness to the absolute borrow cap (distinct from utilization) |
| 6H Borrow APY | Percentage | 6-hour average native borrow APY |
| Real-Time Borrow APY | Percentage | Current native borrow APY. Spiky |
| Merkl Borrow Reward APY | Percentage | Current Merkl reward APY for borrowing |
| 6H Net Borrow APY | Percentage | 6-hour average net borrow APY (native minus Merkl rewards) |
| Net Borrow APY | Percentage | Current net borrow APY (native minus Merkl rewards). Spiky |

## Aave user positions

Wallet-scoped position on a specific Aave V3 market.

| Metric | Type | Description |
|---|---|---|
| Health Factor | Ratio | Below 1.0 is liquidation-eligible. Above 1.5 is typically safe. Renders as ∞ for collateral-only positions |
| Loan-to-Value (LTV) | Percentage | Total debt ÷ total collateral |
| Total Collateral (USD) | USD | Supplied collateral on this market |
| Total Debt (USD) | USD | Outstanding borrows on this market |

## Hyperliquid perp markets

Market-level metrics on a Hyperliquid perp. Scoped by coin (BTC, ETH, HYPE, …), no wallet required.

| Metric | Type | Description |
|---|---|---|
| Mark Price | USD | Current mark price |
| Oracle Price | USD | Off-chain oracle (index) price |
| Mid Price | USD | Midpoint of the order book bid/ask |
| Funding Rate (1H) | Percentage | Last-hour funding rate. Positive = longs pay shorts |
| Open Interest | USD | Total notional open interest |
| 24H Volume | USD | 24-hour notional volume |
| Premium | Percentage | Mark/oracle premium |
| Max Leverage | Multiplier | Maximum leverage Hyperliquid allows |
| Previous Day Price | USD | Mark price 24 hours ago |

## Hyperliquid user positions

Wallet-scoped active perp positions.

| Metric | Type | Description |
|---|---|---|
| Position Size | Asset units | Signed position size. Negative = short |
| Entry Price | USD | Average entry price |
| Mark Price | USD | Current mark price of the underlying perp |
| Leverage | Multiplier | Effective leverage on the position |
| Liquidation Price | USD | Estimated liquidation price |
| Margin Used | USD | Margin currently allocated to the position |
| Unrealized PnL | USD | Unrealized PnL. Negative = losing |
| Position Value | USD | Notional value (\|size\| × mark) |
| Return on Equity | Percentage | Unrealized PnL ÷ margin used |
| Cumulative Funding | USD | All-time cumulative funding (positive = paid) |

## Polymarket

| Metric | Type | Description |
|---|---|---|
| YES Outcome | Percentage | Implied probability of the YES outcome |
| NO Outcome | Percentage | Implied probability of the NO outcome |
| 24h Volume | USD | Total trading volume over the last 24 hours |
| Liquidity | USD | Total liquidity available in the market |
| Spread | Percentage | Bid-ask spread. Smaller = more liquid |
