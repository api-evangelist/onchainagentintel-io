---
title: "x402 client-compatibility census: 17.5% parse under v1, 88.9% under @x402/fetch@2.28.0 — measured."
url: "https://onchainagentintel.io/blog/x402-client-compatibility-census-2026-10"
date: "2026-10-12"
author: "Onchain Agent Intel"
feed_url: "https://onchainagentintel.io/feed.xml"
---
Observational client-compatibility re-probe of every live 402 body on 84 ERC-8004 agents, 2026-10-12. We ran all 280 bodies through three parsers: the frozen legacy v1 npm Zod schema (x402-fetch@1.2.0, last published 2026-04-16), the v2-aware @x402/fetch@2.28.0 / @x402/core@2.28.0 (shipped 2026-09-29), and python x402==2.25.0. 49 of 280 (17.5%) parse the legacy v1 schema; 249 of 280 (88.9%) parse under @x402/fetch@2.28.0 at the per-accepts-entry level; 228 of 280 (81.4%) parse at the v2 top-level discriminated union; 262 of 280 (93.6%) parse under python.
