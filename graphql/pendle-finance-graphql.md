# Pendle Finance GraphQL (Subgraph)

## Description

Pendle Finance exposes on-chain protocol data through a Graph Protocol subgraph (`subgraph-v3`). The subgraph indexes Ethereum mainnet events from the Pendle Router and related contracts, making it possible to query yield contracts, markets (Pairs), token volumes, liquidity positions, swaps, mint/redeem actions, and time-series snapshots over GraphQL without writing custom event listeners.

The subgraph covers the V1/V2 Pendle on-chain data layer — forges, yield contracts (XYT/OT tokens), AMM market pairs, liquidity mining, and supporting integrations with Uniswap and Sushiswap for OT-token trading. For current V2 data at scale, Pendle's Backend Data API (REST) is also available and cross-chain by default.

## Endpoint

- **Legacy Explorer / Hosted Service:** `https://thegraph.com/legacy-explorer/subgraph/ngfam/pendle`
- **Source Repository:** `https://github.com/pendle-finance/subgraph-v3`
- **Network (mainnet):** Ethereum Mainnet — PendleRouter `0x1b6d3E5Da9004668E14Ca39d1553E9a46Fe842B3` (startBlock 12638048)
- **Network (kovan testnet):** PendleRouter `0x85dB6E6eDb8EC6DFeC222B80A54Cc7b42F59671e` (startBlock 25449544)
- **Polygon config:** available in `subgraph-modes/polygon.yaml`

## Documentation

- Pendle Developer Docs: https://docs.pendle.finance/pendle-dev
- Subgraph GitHub Repository: https://github.com/pendle-finance/subgraph-v3
- The Graph Legacy Explorer: https://thegraph.com/legacy-explorer/subgraph/ngfam/pendle
- Pendle Backend Data API Overview: https://docs.pendle.finance/pendle-dev/Backend/ApiOverview

## Key Entity Types

| Entity | Description |
|---|---|
| `Forge` | Pendle forge contracts (Aave forge, Compound forge, etc.) |
| `MarketFactory` | Market factory contracts per forge |
| `YieldContract` | Yield contracts mapping underlying asset + expiry to XYT/OT tokens |
| `Token` | All tokens in the protocol (XYT, OT, yield-bearing, base swap tokens) |
| `Pair` | AMM market pairs (XYT/base token), including reserves, volume, TVL, implied yield |
| `Swap` | Swap events on Pendle AMM pairs |
| `MintYieldToken` | Events minting XYT and OT from a yield-bearing asset |
| `RedeemYieldToken` | Events redeeming XYT and OT back to the underlying |
| `MintLPToken` | Liquidity provision events on Pendle pairs |
| `BurnLPToken` | Liquidity removal events on Pendle pairs |
| `LiquidityPool` | Unified join/exit record for the Pendle AMM |
| `LiquidityPosition` | Per-user LP token balances across pairs |
| `LiquidityPositionSnapshot` | Historical snapshots of LP positions |
| `Transaction` | Top-level transaction entity linking swap/mint/redeem children |
| `PairHourData` | Hourly OHLC, volume, TVL, and implied yield per pair |
| `PairDailyData` | Daily OHLC, volume, TVL, and implied yield per pair |
| `LiquidityMining` | Liquidity mining contract references |
| `User` | Wallet addresses with aggregated swap volume |
| `UserMarketData` | Per-user per-market LP holding, yield claimed, PENDLE rewards |
| `UniswapPool` | Uniswap V3 pools used for price oracles |
| `UniswapTokenPrice` | Derived token prices from Uniswap |
| `SushiswapPair` | Sushiswap pairs used to trade OT tokens |
| `SushiswapPairHourData` | Hourly trading volume for Sushiswap OT pairs |
| `LpTransferEvent` | LP token transfer events with price at time of transfer |
| `PendleData` | Protocol-level fee parameters |
| `DebugLog` | Internal debug log entities (development use) |

## Example Query

```graphql
{
  pairs(first: 5, orderBy: reserveUSD, orderDirection: desc) {
    id
    token0 { symbol }
    token1 { symbol }
    reserveUSD
    volumeUSD
    txCount
    expiry
    lpAPR
  }
}
```

```graphql
{
  yieldContracts(first: 10) {
    id
    forgeId
    expiry
    underlyingAsset { symbol }
    xyt { symbol }
    ot { symbol }
    lockedVolumeUSD
    mintVolume
    redeemVolume
  }
}
```
