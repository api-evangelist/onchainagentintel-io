---
generated: '2026-09-19'
method: generated
name: Buy a 30-day flat-rate subscription and query intel with it
description: Pay once over x402 for 30 days of unlimited /v1/intel/* calls, confirm activation, then pass your wallet on every intel call instead of paying per request.
api: openapi/onchainagentintel-io-openapi.yml
operations: [paid_agent_intel_subscribe_post, paid_agent_intel_trending_get, paid_agent_intel_delta_get, paid_agent_intel_search_post]
source: >-
  operationIds verified in openapi/onchainagentintel-io-openapi.yml; subscription semantics from
  https://onchainagentintel.io/docs (Subscription and Subscription Status sections) and
  https://onchainagentintel.io/services. Note: the free status poll GET /v1/intel/subscription/{sub_id}
  is documented and answers live (404 {"detail":"Subscription not found"} for an unknown id) but is NOT
  in the published OpenAPI, so it has no operationId to cite.
---

# Buy a 30-day flat-rate subscription and query intel with it

For an agent that will make more than ~25 profile lookups a month, one $5.00 USDC payment (0.002 ETH) replaces per-call x402 on seven intel endpoints for 30 days.

## Auth
- x402 only; no account. See `authentication/onchainagentintel-io-authentication.yml`.

## Money rules
- Price and payTo come from the 402 body / `well-known/onchainagentintel-io-x402.json`. The 402 for the subscription carries an OFFER window (`expires_at`, 15 minutes in the docs example); the subscription itself runs 30 days from `paid_at`.
- The purchase is an on-chain settlement with no documented refund or cancel; the "cancel anytime" language on the pricing page applies to the separate $19/mo Pro web plan billed through Stripe, not to this x402 subscription. See `conventions/onchainagentintel-io-conventions.yml` (reversibility).

## Steps
1. **Request the offer** — `paid_agent_intel_subscribe_post` (`POST /v1/intel/subscribe`). The 402 body returns `sub_id`, a `preview.covers` list (`trending, delta, market, peers, agent_profile, search, graph`), `payment_options[]` and `expires_at`.
2. **Pay** — either retry with `X-PAYMENT` (EIP-3009 USDC) or send exactly the quoted ETH to the Safe with calldata `SUB-{sub_id}`.
3. **Confirm activation** — poll `GET /v1/intel/subscription/{sub_id}` (free, undocumented in the spec — see source note) until `status` is `ACTIVE` (`PENDING | ACTIVE | EXPIRED`); the body also returns `subscriber_addr`, `paid_at`, `expires_at`, `payment_tx`, `payment_chain`.
4. **Query with the wallet** — pass `wallet=<subscriber_addr>` on every covered call: `paid_agent_intel_trending_get` (`GET /v1/intel/trending?wallet=…`), `paid_agent_intel_delta_get` (`GET /v1/intel/delta?since=<unix>&wallet=…`), `paid_agent_intel_search_post` (`POST /v1/intel/search`, JSON body with `capabilities[]`, `chain`, `bucket`). A call with an active wallet returns 200 directly instead of 402.
5. **Renew** — after `expires_at` the wallet falls back to per-call 402s; repeat from step 1. Audit (`/v1/audit`) and evaluate (`/v1/evaluate`) are NOT covered by the subscription and stay per-call at $10 USDC.

## Errors
- `402` on a covered call after paying means the subscription is not yet `ACTIVE` or the `wallet` query param is missing/mismatched (the docs lowercase `subscriber_addr`). See `errors/onchainagentintel-io-problem-types.yml`.
