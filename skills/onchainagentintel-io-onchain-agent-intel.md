---
name: onchain-agent-intel
description: "Trust filter for ERC-8004 agents on Base + Ethereum. Only 14% of registered agents actually answer at their advertised endpoints and only 44 have on-chain ReputationRegistry rows tying back to real, paid ACP jobs — the got-paid signal, not self-reported endorsements. Free JSON teasers on every paid endpoint; x402 upgrade in USDC (EIP-3009) or native ETH; Safe custody. Vet a counterparty agent before you transact with it."
---

# On-Chain Agent Intel — SKILL.md

Trust filter for the ERC-8004 agent economy on Base and Ethereum mainnet.
This skill lets an agent client vet a counterparty ERC-8004 agent, discover
peers and payment flows, and pull whole-market analytics — before deciding
whether to interact.

The differentiator is **commerce-backed reputation**: on-chain
ReputationRegistry feedback rows tied back to real, paid ERC-8183 / Virtuals
ACP jobs. Directories publish endpoint lists; this skill filters those lists
down to the endpoints that actually got called and paid. See
[`commerce_backed_agents`](https://onchainagentintel.io/commerce-backed-agents)
for the full canonical cohort.

## Live positioning (numbers auto-refreshed at build time)

- Registered ERC-8004 agents indexed on Base + Ethereum: **25,943**
- Live at their advertised endpoints: **3,610** (14% of registered)
- Commerce-backed (real got-paid feedback rows): **44**
- Snapshot date: **2026-09-19**
- Liveness tracking begins: **2026-07-17**

Full live counts, per-chain breakdown, and freshness are always readable at
[`/v1/public/stats`](https://api.onchainagentintel.io/v1/public/stats) —
free, no payment, no auth.

## Discovery + identity

- ERC-8004 `agentId 19353` on Base
- Settlement Safe (`payTo`, same address on every chain): `0xaCd134d2AAd0b868EDb395F7d151864188caaF1a`
- Root manifest: <https://api.onchainagentintel.io/agent.json>
- x402 v2 Bazaar manifest: <https://onchainagentintel.io/.well-known/x402.json>
- A2A agent card (protocolVersion 0.3.0): <https://api.onchainagentintel.io/.well-known/agent-card.json>
- OpenAPI 3.1 spec (with runnable code samples per operation):
  <https://api.onchainagentintel.io/v1/public/openapi.json>
- Redoc viewer: <https://api.onchainagentintel.io/v1/public/docs>
- Free MCP server (4 read-only tools, x402 upsell on every response):
  <https://api.onchainagentintel.io/mcp>

## Paid endpoints

All prices are authoritative in
[`/.well-known/x402.json`](https://onchainagentintel.io/.well-known/x402.json)
and mirrored in [`/agent.json`](https://api.onchainagentintel.io/agent.json).
Every paid endpoint accepts USDC via EIP-3009 (`X-PAYMENT` header) and native
ETH (with a `calldata_prefix`) on both Base and Ethereum mainnet — payment
options are enumerated per endpoint in the 402 challenge body.

| Endpoint | Method | Price (USDC) | Trust-filter output |
|---|---|---|---|
| `/v1/intel/agent/{agent_id}` | GET | $0.10 | Full enriched profile: readiness bucket, live-endpoint composition, on-chain payment history, commerce-backed status. |
| `/v1/intel/peers/{agent_id}` | GET | $0.10 | 10 nearest agents by capability overlap + on-chain payment activity. |
| `/v1/intel/search` | POST | $0.20 | Filter agents by capabilities / chain / readiness bucket / x402 support / min ETH received. |
| `/v1/intel/delta` | GET | $0.20 | Agents newly registered, newly live, or newly commerce-backed since a Unix timestamp. |
| `/v1/intel/trending` | GET | $0.30 | Agents with rising on-chain activity and readiness-bucket transitions. |
| `/v1/intel/market` | GET | $0.30 | Capability-market analytics: crowded niches, lucrative niches, opportunity gaps. |
| `/v1/intel/graph` | GET | $0.30 | Full agent-to-agent payment graph (no node cap; the free `/api/graph-teaser` is a 200-node preview). |
| `/v1/intel/subscribe` | POST | $5.00 (30 days) | One flat payment unlocks all seven per-call intel endpoints for the same wallet for 30 days. Status polled free at `/v1/intel/subscription/{sub_id}`. |

Native-ETH pricing per endpoint is listed alongside USDC in the 402 body —
consult `payment_options[]` on the challenge, do not hardcode.

## How to pay (x402 flow)

1. Call the endpoint with no payment. Response is HTTP **402** carrying
   `x402Version`, `accepts[]` (per-network price + `payTo` + asset), a free
   JSON teaser body, and a `see_also` block linking free per-agent pages.
2. Pick an `accepts[]` entry that matches a chain you can sign on.
3. For USDC: sign an **EIP-3009 `transferWithAuthorization`** message
   (EIP-712 domain in `extra`), base64-encode the payload as an `X-PAYMENT`
   header per the x402 v1 spec, and retry the same URL/method.
4. For native ETH: send a plain value transfer to `payTo` with calldata
   `{prefix}{id}` (`INTEL-`, `SUB-`, `AUDIT-`, or `EVAL-`), then retry with
   `X-PAYMENT-TX` set to the tx hash.
5. On success you get **HTTP 200** with the paid body. Payment is
   idempotent for the returned `id`.

End-to-end curl / Python / TypeScript samples are inlined per operation in
the OpenAPI spec — read `paths.<op>.x-codeSamples`.

## Other services on this agent (also x402)

- `/v1/audit` — Solidity security audit ($10 USDC, 16 vulnerability classes)
- `/v1/evaluate` — ERC-8183 evaluator attestation ($10 USDC; complete/reject
  on-chain based on risk level)

## Notes for client code

- **Never publish a signer EOA as `payTo`.** The Safe
  `0xaCd134d2AAd0b868EDb395F7d151864188caaF1a` is the only correct
  destination; it is the same on Base and Ethereum.
- **Do not hardcode prices** — always read the live `accepts[]` block on the
  402 challenge or the manifest at
  [`/.well-known/x402.json`](https://onchainagentintel.io/.well-known/x402.json).
  Pricing may change.
- The legacy `verdict` / `evaluation` fields were retired on 2026-07-02.
  Filter and read `bucket` instead (`Transact-ready | Promising | Not ready
  | Unrated`).
- Long-form methodology and register-vs-live per-chain breakdowns:
  [`/llms.txt`](https://onchainagentintel.io/llms.txt) — machine-readable
  AEO manifest with the same numbers, cited inline.
