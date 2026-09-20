---
generated: '2026-09-19'
method: generated
name: Vet a counterparty ERC-8004 agent before transacting
description: Check a counterparty ERC-8004 agent's free objective signals, then buy its full trust profile and nearest peers over x402.
api: openapi/onchainagentintel-io-openapi.yml
operations: [public_v1_public_agent_chain_agent_id_get, paid_agent_intel_profile_get, paid_agent_intel_peers_get]
source: >-
  operationIds verified in openapi/onchainagentintel-io-openapi.yml (fetched from
  https://api.onchainagentintel.io/v1/public/openapi.json 2026-09-19); x402 flow from the provider's
  SKILL.md and https://onchainagentintel.io/docs#x402-flow; prices from /.well-known/x402.json.
---

# Vet a counterparty ERC-8004 agent before transacting

Decide whether an ERC-8004 agent is reachable, payable and trusted before wiring funds to it.

## Auth
- No account, no API key. Paid operations are x402-gated: the first call returns HTTP 402 and you retry with an `X-PAYMENT` header (USDC via EIP-3009) or `X-PAYMENT-TX` (native ETH). See `authentication/onchainagentintel-io-authentication.yml`.

## Money rules
- Read the price from the live 402 `accepts[]` block or `well-known/onchainagentintel-io-x402.json`; never hardcode it. The profile lookup was $0.10 USDC on Base at capture.
- Pay ONLY to the Safe `0xaCd134d2AAd0b868EDb395F7d151864188caaF1a` (same on Base and Ethereum) — the address every 402 body and manifest names.
- Use a fresh random EIP-3009 nonce per request; the authorization `validBefore` window in the docs example is 300 seconds. Settlement is on-chain and not reversible — see `conventions/onchainagentintel-io-conventions.yml`.

## Steps
1. **Free look first** — `public_v1_public_agent_chain_agent_id_get` (`GET /v1/public/agent/{chain}/{agent_id}`, `chain` is `base` or `ethereum`). Read `objective_signals` (reachable, http_status, tls_valid, x402_supported, payments_received, mcp_tool_count, openapi_method_count, owner_named) and `status_label`. An unknown agent returns 404; a non-integer id returns 422. If `reachable` is false or `status_label` is "Stub or unreachable", stop here — nothing to buy.
2. **Buy the full profile** — `paid_agent_intel_profile_get` (`GET /v1/intel/agent/{agent_id}?chain=base`). Expect 402 with a `preview` (counts only) and `accepts[]`; sign an EIP-3009 `transferWithAuthorization` for the chosen `accepts[]` entry, base64-encode the x402 v1 payload, retry with `X-PAYMENT`. The 200 body carries the readiness bucket (`Transact-ready | Promising | Not ready | Unrated`), sub-scores (live / payable / reputable / active), resolved owner identity, live endpoint inventories and on-chain payment history. Do not read the retired `verdict` / `evaluation` fields (removed 2026-07-02).
3. **Compare against peers (optional)** — `paid_agent_intel_peers_get` (`GET /v1/intel/peers/{agent_id}`, $0.10 USDC) returns the 10 nearest agents by capability overlap and payment activity, so you can pick a better-scored alternative before committing.
4. **Decide** — treat only the commerce-backed reputation subset as a trust signal; the unfiltered ReputationRegistry count can be written by anyone (provider's own methodology at https://onchainagentintel.io/can-you-trust-an-erc-8004-reputation-score).

## Errors
- `402` — payment challenge, not a failure; `accepts[]` is the price list. `404` — agent or subscription not found (`{"detail": ...}`). `422` — FastAPI validation `detail[]`. See `errors/onchainagentintel-io-problem-types.yml`.
