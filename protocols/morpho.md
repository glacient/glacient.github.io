---
title: Morpho
eyebrow: Protocols
summary: Watch Morpho vaults and markets across Ethereum, Base, Arbitrum, and HyperEVM.
permalink: /protocols/morpho/
---

Glacient supports both Morpho **vaults** and **markets** with first-class collection types. The collection you pick determines which metrics are available.

## Coverage

| Surface | Chains | Versions |
|---|---|---|
| Vaults | Ethereum, Base, Arbitrum, HyperEVM | Morpho V1 and V2 |
| Markets | Ethereum, Base, Arbitrum, HyperEVM | n/a |

If you explicitly say "V1" or "V2" in the AI prompt, Glacient preserves that qualifier when resolving the vault. Without a qualifier, the resolver probes both in parallel and surfaces the match.

## Referring to a vault

You can identify a Morpho vault in three ways:

- **By name.** `Steakhouse PYUSD`, `Gauntlet USDC`, `Spark DAI`. The resolver uses Morpho's public search.
- **By address.** A `0x` + 40-hex address. Resolved directly.
- **By My Investments.** Connect a wallet and pick from vaults you've already deposited into. Read-only.

## Referring to a market

Markets are identified by the **collateral / loan token pair** as one string, not split across fields:

- `cbBTC USDT market`
- `WETH USDC market`
- `wstETH WETH market`

If you have the 64-hex market ID, paste it directly and Glacient fetches the market by ID without a search round-trip.

## Vault metrics

Supply-side metrics available on Morpho vault collections:

| Metric | Description |
|---|---|
| 6H Supply APY (Net) | 6-hour average net supply APY, includes rewards and after fees |
| 6H Supply APY (Native) | 6-hour average native supply APY, excludes rewards |
| Real-Time Net Supply APY | Current net supply APY (includes rewards, after fees). Spiky |
| Real-Time Native Supply APY | Current native supply APY (excludes rewards). Spiky |
| Liquidity | Total value locked in the vault |
| Token | Vault's deposit token |

## Market metrics

Supply-side metrics available on Morpho market collections:

| Metric | Description |
|---|---|
| 6H Supply APY (Net) | 6-hour average net supply APY, includes rewards |
| 6H Supply APY (Native) | 6-hour average native supply APY, excludes rewards |
| Real-Time Net Supply APY | Current net supply APY (includes rewards). Spiky |
| Real-Time Native Supply APY | Current native supply APY (excludes rewards). Spiky |
| Liquidity | Total liquidity available in the market |
| Token | Market's loan token |

## Typical workflows

- **Yield monitoring.** `Steakhouse PYUSD` vault, **6H Supply APY (Net)** below 4% → Telegram alert.
- **Smoothed rate watch.** `cbBTC USDT` market, **6H Supply APY (Native)** below 2% → Telegram alert. The 6H window dampens the noise of the real-time read.
- **Liquidity drain.** Vault, **Liquidity** below your floor → Telegram alert.

See [Workflows](/concepts/workflows/) for the model. See [Metrics catalog](/reference/metrics/) for the full list of available metrics across protocols.
