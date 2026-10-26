# Pendle Finance (pendle-finance)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Pendle Finance is a decentralized yield-trading protocol that tokenizes future yield by stripping yield-bearing assets into Principal Tokens (PT) and Yield Tokens (YT) wrapped in a Standardized Yield (SY) layer. PT trades at a discount and matures one-to-one for the underlying at expiry, giving buyers a fixed yield; YT entitles holders to the variable yield until expiry, letting them long, hedge, or speculate on yield itself. Pendle V2 pairs this with a purpose-built AMM for trading time-decaying assets, and Boros extends the design into a margin venue for trading yield as a perpetual rate. The protocol is live on Ethereum, Arbitrum, BNB Chain, Optimism, Base, Mantle, Sonic, Berachain, HyperEVM, Monad, Katana, and Ink. Developer surface includes the Pendle Hosted SDK (a REST API for generating Pendle transactions), a Backend Data API for market, asset, price, and governance data, Socket.IO real-time feeds, the Boros TypeScript SDK and Boros HTTP API, vePENDLE / sPENDLE governance, and audited open-source Solidity contracts for V2 cores, SY wrappers, and Boros core.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/pendle-finance/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - DeFi, Yield Trading, Yield Stripping, Principal Tokens, Yield Tokens, Standardized Yield, AMM, Fixed Yield, Perpetual Yield, vePENDLE, Boros, EVM

## Timestamps

- **Created:** 2026-05-24
- **Modified:** 2026-05-24

## APIs

### Pendle Hosted SDK API
A hosted REST API that generates ready-to-broadcast calldata for every Pendle protocol action — swap (including tokens-to-PT, PT-to-tokens, YT swaps), add and remove liquidity, ZPI (zero-price-impact) flows, mint and redeem PT/YT, mint and redeem SY, transfer liquidity, roll over PT positions, and dual-sided liquidity. Most operations go through a single universal Convert endpoint (`POST /v3/sdk/{chainId}/convert`) that accepts tokens in, tokens out, amounts, receiver, slippage, optional aggregator selection (KyberSwap, etc.), and additional analytics flags (impliedApy, effectiveApy). The hosted SDK tracks Pendle UI behaviour exactly and is updated whenever underlying SY assets evolve, so integrators do not have to patch client SDKs to follow protocol changes.

**Human URL:** [https://docs.pendle.finance/pendle-dev/Backend/HostedSdk](https://docs.pendle.finance/pendle-dev/Backend/HostedSdk)

#### Tags:

 - SDK, Hosted API, Transactions, Swap, Liquidity, Mint, Redeem

#### Properties

- [Documentation](https://docs.pendle.finance/pendle-dev/Backend/HostedSdk)
- [APIReference](https://api-v2.pendle.finance/core/docs)
- [Examples](https://github.com/pendle-finance/pendle-examples-public/tree/main/hosted-sdk-demo)

### Pendle Backend Data API
REST API for offchain Pendle data — markets, assets, prices, user positions, transactions, points, and governance. Cross-chain endpoints (`GET /v2/markets/all`, `GET /v1/assets/all`, `GET /v1/prices/assets`) return data spanning every supported chain in one call and are the recommended entry points for new integrations. Chain-scoped endpoints (`/v3/{chainId}/markets/{address}/historical-data`, `/v5/{chainId}/transactions/{address}`) provide deep market history with optional APY breakdown and per-address transaction history. The pricing response includes a partial-success `errors` array so callers can handle non-fatal missing-asset cases without retrying.

**Human URL:** [https://docs.pendle.finance/pendle-dev/Backend/ApiOverview](https://docs.pendle.finance/pendle-dev/Backend/ApiOverview)

#### Tags:

 - Backend API, Markets, Assets, Prices, Governance, Analytics

#### Properties

- [Documentation](https://docs.pendle.finance/pendle-dev/Backend/ApiOverview)
- [APIReference](https://api-v2.pendle.finance/core/docs)

### Pendle Real-Time Feeds (Socket.IO)
Real-time data feeds delivered over Socket.IO from `https://api-v2.pendle.finance/pendle-v2`. Clients connect once over WebSocket and subscribe to per-feed room ids to receive order-book snapshots and other push updates without polling. The limit-order order-book feed pushes a fresh snapshot every five seconds for every whitelisted market at four precision levels and mirrors the payload shape of the REST endpoint `GET /limit-order/v2/order-book/:chainId`.

**Human URL:** [https://docs.pendle.finance/pendle-dev/Backend/SocketIO](https://docs.pendle.finance/pendle-dev/Backend/SocketIO)

#### Tags:

 - Real-Time, WebSocket, Socket.IO, Order Book, Streaming

#### Properties

- [Documentation](https://docs.pendle.finance/pendle-dev/Backend/SocketIO)

### Pendle Router Static (On-chain Helper)
RouterStatic is an on-chain read-only helper contract that exposes simulation and quoting functions used by the Pendle SDK and frontend — previewing swap, mint, redeem, and liquidity outcomes without submitting a transaction. Integrators can call RouterStatic directly from any web3 client to drive custom quoting, analytics, or trade simulation flows.

**Human URL:** [https://docs.pendle.finance/pendle-dev/Backend/RouterStatic](https://docs.pendle.finance/pendle-dev/Backend/RouterStatic)

#### Tags:

 - Smart Contracts, Read-Only, Quotes, Simulation

#### Properties

- [Documentation](https://docs.pendle.finance/pendle-dev/Backend/RouterStatic)

### Pendle Boros HTTP API
REST API for the Boros margin trading venue — querying markets, account positions, orders, fills, funding, and historical data, and submitting signed orders generated via the Boros SDK. Boros lets traders take leveraged long or short positions on yield rates with a cross-margin or isolated-margin account model and an Agent trading pattern that delegates signing to scoped subaccounts. The HTTP API is the integration backbone for bots, market-makers, and analytics.

**Human URL:** [https://docs.pendle.finance/boros-dev/Backend/api](https://docs.pendle.finance/boros-dev/Backend/api)

#### Tags:

 - Boros, Margin, Trading, Yield Perpetuals, HTTP API

#### Properties

- [Documentation](https://docs.pendle.finance/boros-dev/Backend/api)
- [Overview](https://docs.pendle.finance/boros-dev/Backend/overview)

### Pendle Boros SDK
Official TypeScript SDK (`@pendle/boros-sdk-public`) that wraps calldata generation, EIP-712 signing, the Agent trading model, and Send-Txs-Bot dispatch on top of the Boros HTTP API. Uses `viem` 2.x as a peer dependency and pairs with `@pendle/boros-offchain-math` for tick/rate conversion. Exposes a high-level `Exchange` client with methods like `placeOrder`, `getAllMarkets`, plus an escape-hatch `getOpenApiSdk()` for direct OpenAPI access.

**Human URL:** [https://docs.pendle.finance/boros-dev/Backend/sdk](https://docs.pendle.finance/boros-dev/Backend/sdk)

#### Tags:

 - Boros, SDK, TypeScript, Margin, Trading

#### Properties

- [Documentation](https://docs.pendle.finance/boros-dev/Backend/sdk)
- [Repository](https://github.com/pendle-finance/boros-sdk-public)
- [Package](https://www.npmjs.com/package/@pendle/boros-sdk-public)
- [Quickstart](https://docs.pendle.finance/boros-dev/Backend/bot-quickstart)
- [Examples](https://github.com/pendle-finance/boros-api-examples)

### Pendle V2 Core Smart Contracts
Open-source Solidity implementation of the Pendle V2 protocol — Router, MarketFactory, Market, PT, YT, vePENDLE, fee distributor, governance, and supporting libraries. Distributed on npm as `@pendle/core-v2`, allowing other Solidity projects to import the interfaces directly. Deployed to Ethereum (chain 1), Optimism (10), BNB Chain (56), Sonic (146), Monad (143), HyperEVM (999), Mantle (5000), Base (8453), Arbitrum (42161), Ink (57073), Berachain (80094), and Katana (747474). Audited by six independent firms with reports kept in the `audits` folder of the public repo.

**Human URL:** [https://github.com/pendle-finance/pendle-core-v2-public](https://github.com/pendle-finance/pendle-core-v2-public)

#### Tags:

 - Smart Contracts, Solidity, V2, EVM, Router, vePENDLE

#### Properties

- [Repository](https://github.com/pendle-finance/pendle-core-v2-public)
- [Package](https://www.npmjs.com/package/@pendle/core-v2)
- [Deployments](https://docs.pendle.finance/pendle-dev/Deployments)
- [V2Resources](https://github.com/pendle-finance/pendle-v2-resources)

### Pendle SY (Standardized Yield) Contracts
Public repository of Standardized Yield (SY) wrapper contracts that adapt every supported yield-bearing asset (LSTs, LRTs, stablecoin vaults, RWA tokens, etc.) into a single ERC-20 surface that Pendle V2 Markets understand. New asset listings ship as new SY contracts in this repo, paired with deployment scripts in `Pendle-SY-Public` and tests in `pendle-sy-tests`.

**Human URL:** [https://github.com/pendle-finance/Pendle-SY-Public](https://github.com/pendle-finance/Pendle-SY-Public)

#### Tags:

 - Smart Contracts, Solidity, SY, ERC-5115, Wrappers

#### Properties

- [Repository](https://github.com/pendle-finance/Pendle-SY-Public)
- [Tests](https://github.com/pendle-finance/pendle-sy-tests)
- [Deployment](https://github.com/pendle-finance/Pendle-Market-Deployment)

### Pendle Boros Core Smart Contracts
Open-source Solidity core for Boros — the order-book / margin venue that lets traders long or short yield rates with leverage. Contracts cover the exchange, market accounts, agent authorization, settlement, and risk engine. Designed to integrate with the Boros HTTP API and Boros SDK for the off-chain orderbook and signed-order flow.

**Human URL:** [https://github.com/pendle-finance/boros-core-public](https://github.com/pendle-finance/boros-core-public)

#### Tags:

 - Smart Contracts, Solidity, Boros, Margin, Orderbook

#### Properties

- [Repository](https://github.com/pendle-finance/boros-core-public)

## Common Properties

- [Website](https://www.pendle.finance/)
- [App](https://app.pendle.finance)
- [Boros](https://boros.pendle.finance)
- [Documentation](https://docs.pendle.finance)
- [DeveloperDocs](https://docs.pendle.finance/pendle-dev)
- [BorosDocs](https://docs.pendle.finance/boros-dev)
- [APIReference](https://api-v2.pendle.finance/core/docs)
- [Markets](https://app.pendle.finance/trade/markets)
- [Governance](https://app.pendle.finance/vependle)
- [GitHubOrganization](https://github.com/pendle-finance)
- [Repository](https://github.com/pendle-finance/pendle-core-v2-public)
- [Blog](https://medium.com/pendle)
- [Twitter](https://twitter.com/pendle_fi)
- [Discord](https://pendle.finance/discord)
- [Telegram](https://t.me/pendle_info_bot)
- [Pendle Core V2 npm Package (SDK)](https://www.npmjs.com/package/@pendle/core-v2)
- [Pendle Boros SDK npm Package (SDK)](https://www.npmjs.com/package/@pendle/boros-sdk-public)
- [Examples](https://github.com/pendle-finance/pendle-examples-public)

## Features

| Name | Description |
|------|-------------|
| Yield Stripping (PT and YT) | Splits any yield-bearing asset into a Principal Token redeemable one-to-one at expiry and a Yield Token capturing every unit of yield until expiry, letting users trade the two halves independently. |
| Standardized Yield (SY) Wrappers | ERC-5115 inspired wrappers normalize hundreds of LSTs, LRTs, stablecoin vaults, and RWA tokens into a single token interface that Pendle V2 markets and AMM understand. |
| Fixed Yield Trading | Buying PT at a discount locks in a fixed APY through expiry, regardless of how the underlying floating yield evolves. |
| Leveraged Yield Exposure (YT) | Buying YT gives capital-efficient long exposure to floating yield without holding the principal, used to long, hedge, or speculate on yield rates. |
| Time-Decay AMM | Purpose-built AMM that prices PT and YT against the underlying while accounting for time-to-expiry, supporting deep liquidity for yield trading. |
| vePENDLE Governance and Boosts | Locking PENDLE into vePENDLE grants governance power, voting on gauge weights, fee share, and LP yield boosts across markets. |
| Boros — Yield as a Perpetual | Margin trading venue that turns variable yield rates into perpetual instruments with leverage, cross-margin, isolated margin, and an Agent trading model. |
| Multi-Chain Deployment | Live on Ethereum, Arbitrum, BNB Chain, Optimism, Base, Mantle, Sonic, Berachain, HyperEVM, Monad, Katana, and Ink — markets and PT/YT pairs deployed per chain. |
| Hosted SDK for Drop-In Integration | A single Convert endpoint generates calldata for every protocol action so integrators never have to patch a client SDK as underlying SY assets evolve. |
| Cross-Chain Backend Data | `/v2/markets/all`, `/v1/assets/all`, and `/v1/prices/assets` return data across every supported chain in a single request, with pagination, points data, and partial-success error reporting. |
| Real-Time Order-Book Feeds | Socket.IO order-book streams push snapshots every five seconds for every whitelisted market at four precision levels. |

## Use Cases

| Name | Description |
|------|-------------|
| Fixed-Yield Vault | Wrap PT purchases into a vault product that delivers a fixed APY on stablecoins or ETH-denominated LSTs until expiry. |
| Yield Speculation Desk | Use YT to take leveraged directional positions on a specific asset's yield without holding the principal collateral. |
| Points / Airdrop Maximization | Stack ecosystem points (eigenlayer, ethena, etc.) by holding YT of point-bearing assets, with `/v2/markets/all` exposing per-market points metadata. |
| LP Strategy Optimizer | Auto-rebalance liquidity across Pendle pools using the Hosted SDK Convert API for add/remove/transfer-liquidity and the Backend Data API for APY breakdown. |
| Boros Yield Trading Bot | Quote-driven market-making or directional bot on Boros markets using the Boros SDK, Send-Txs Bot, and Socket.IO order-book feed. |
| DeFi Portfolio Analytics | Build dashboards over Pendle positions using historical APY breakdown, transaction history, and price endpoints. |
| Cross-Chain Yield Aggregation | Aggregate Pendle markets across 12+ EVM chains via the cross-chain REST endpoints for unified yield discovery and routing. |

## Integrations

| Name | Description |
|------|-------------|
| Ethereum | Mainnet deployment (chain id 1) — flagship Pendle markets and vePENDLE governance. |
| Arbitrum | Arbitrum One (42161) — heavy LRT and stablecoin yield activity. |
| BNB Chain | BNB Chain (56) — Pendle markets for BNB-ecosystem yield assets. |
| Optimism | Optimism (10) — Pendle markets for OP-stack yield assets. |
| Base | Base (8453) — Coinbase L2 Pendle markets. |
| Mantle | Mantle (5000) — Pendle markets for Mantle-native yield assets. |
| Sonic | Sonic (146) — Pendle markets on the Sonic chain. |
| Berachain | Berachain (80094) — Pendle markets tied to BGT and PoL yield assets. |
| HyperEVM | HyperEVM (999) — Pendle markets on the Hyperliquid EVM. |
| Monad | Monad (143) — Pendle markets on the Monad chain. |
| Katana | Katana (747474) — Pendle markets on the Katana chain. |
| Ink | Ink (57073) — Pendle markets on the Ink L2. |
| KyberSwap | Default aggregator integrated by the Hosted SDK Convert endpoint for ZAP-in token routing. |
| viem | Required peer dependency for the Boros TypeScript SDK. |
| Send Txs Bot | Boros transaction-dispatch service used by the Boros SDK for signed-order delivery. |

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
