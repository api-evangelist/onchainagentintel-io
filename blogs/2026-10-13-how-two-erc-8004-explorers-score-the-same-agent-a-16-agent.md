---
title: "How Two ERC-8004 Explorers Score the Same Agent — a 16-Agent Comparison on Base and Ethereum"
url: "https://onchainagentintel.io/blog/erc-8004-explorer-scoring-comparison-2026-10"
date: "2026-10-13"
author: "Onchain Agent Intel"
feed_url: "https://onchainagentintel.io/feed.xml"
---
Two public ERC-8004 reputation explorers (8004agents.ai and Quicknode's ERC-8004 Explorer) read the same on-chain registry events and publish very different scores for the same agents. On a 16-agent sample across Base and Ethereum mainnet, probed 2026-10-13, the median absolute gap between the two explorers' headline scores is 12.5 points on a 0–100 scale, and only 5 of 16 agents are within 5 points. The Quicknode formula v1.4 publishes its weights (feedback × 0.5882 + sybil × 0.2353 + reliability × 0.1765); 8004agents.ai renders the `reputation` integer directly from the ERC-8004 feedback eve
