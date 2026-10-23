---
title: "How many ERC-8004 agents can actually take an x402 payment? We probed all 412 endpoints."
url: "https://onchainagentintel.io/blog/how-many-erc8004-agents-can-take-x402-payment"
date: "2026-10-12"
author: "Onchain Agent Intel"
feed_url: "https://onchainagentintel.io/feed.xml"
---
Observational probe of every x402 endpoint advertised in the on-chain metadata of 84 ERC-8004 agents on Base and Ethereum mainnet, 2026-10-11. One unauthenticated request per endpoint; no `X-PAYMENT` header, no signature, no payment. Parses `accepts[]` from three live shapes (JSON body top-level, nested `x402.accepts`, `Payment-Required: ` header).
