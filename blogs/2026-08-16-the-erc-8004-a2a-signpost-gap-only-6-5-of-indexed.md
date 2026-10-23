---
title: "The ERC-8004 → A2A Signpost Gap: Only 6.5% of Indexed Registrations Publish a Discoverable agent-card.json"
url: "https://onchainagentintel.io/blog/the-erc-8004-signpost-gap"
date: "2026-08-16"
author: "Onchain Agent Intel"
feed_url: "https://onchainagentintel.io/feed.xml"
---
Measured 2026-08-16: of 24,835 indexed Base + Ethereum ERC-8004 registrations, only 1,604 (6.5%) publish a discoverable /.well-known/agent-card.json — the standard A2A capability manifest an autonomous discovery client needs to walk from the on-chain identity to a payable endpoint. Hop-by-hop traversal audit over seven live agents shows H1 (registry read), H2 (URI resolve) and H5 (V2 402 paywall shape) all 7/7 PASS; H3 (agent-card discovery) is the single binding hop. Includes concrete named examples of both the failure (ClawFresh agentId 20992 on Base, Name Whisper agentId 29402 on Ethereum) 
