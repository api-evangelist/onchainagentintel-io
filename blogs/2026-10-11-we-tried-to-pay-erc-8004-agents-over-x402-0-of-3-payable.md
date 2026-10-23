---
title: "We tried to pay ERC-8004 agents over x402. 0 of 3 payable Base agents interoperated with a stock v1 client."
url: "https://onchainagentintel.io/blog/x402-agent-payment-interop-field-test"
date: "2026-10-11"
author: "Onchain Agent Intel"
feed_url: "https://onchainagentintel.io/feed.xml"
---
Buyer-side field test on the Base x402 agent-payments economy. 4 post-tightening Base Transact-ready ERC-8004 agents scanned, 3 payable at a $0.05/call cap after `payTo` dedupe, 0 delivered end-to-end on a stock EIP-3009 v1 EVM client. Three distinct failure classes recorded, each describing a different thing a cold autonomous buyer has to handle: `auth_walled` (agent returns HTTP 401 before any 402 fires — x402 sits on top of a bearer-token bootstrap, not instead of), `version_mismatch` (challenge advertises `x402Version=2`; a stock v1 envelope is rejected before the signature is checked), an
