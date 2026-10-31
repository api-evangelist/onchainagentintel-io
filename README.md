# Agent Zero

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

Agent Zero (On-Chain Agent Intel, onchainagentintel.io) is an agent-native intelligence service for the ERC-8004 agent economy: it continuously indexes the ERC-8004 agents registered on Base and Ethereum, probes their advertised MCP, OpenAPI and .well-known endpoints for liveness, joins on-chain payment activity and ReputationRegistry rows, and scores each agent for buyer-POV readiness and trust. The intelligence is sold per call over the x402 protocol (USDC via EIP-3009 or native ETH, no accounts, no API keys) through a 25-operation OpenAPI 3.1 REST API at https://api.onchainagentintel.io, a free anonymous remote MCP server at /mcp, an A2A agent card at /.well-known/agent-card.json, an x402 Bazaar discovery manifest, an llms.txt and a published Agent Skill. It also sells Solidity security audits and ERC-8183 deliverable evaluations, and is itself ERC-8004 agentId 19353 on Base.

**Areas:** Agents · Agent Intelligence · ERC-8004 · x402 · Agentic Commerce · Blockchain · Ethereum · Base · Web3 · MCP · A2A · Smart Contracts

## Agent Zero on APIs.io

Everything profiled for Agent Zero is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/onchainagentintel-io/](https://apis.io/providers/onchainagentintel-io/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [Agent Zero MCP Server](https://apis.io/apis/onchainagentintel-io/agent-zero-mcp-server/) — Free, anonymous remote Model Context Protocol server at https://api.onchainagentintel.io/mcp (Streamable HTTP, protocol version 2025-06-18, serverInfo…
- [Agent Zero A2A Agent](https://apis.io/apis/onchainagentintel-io/agent-zero-a2a-agent/) — Agent2Agent surface: an agent card served from https://onchainagentintel.io/.well-known/agent-card.json (mirrored on www and api hosts) naming the JSON-RPC…
- [Agent Zero Paid X402 API](https://apis.io/apis/onchainagentintel-io/onchainagentintel-io-paid-x402-api/) — Paid endpoints — settle with X-PAYMENT header per x402.
- [Agent Zero Public API](https://apis.io/apis/onchainagentintel-io/onchainagentintel-io-public-api/) — Free endpoints — no payment, no auth.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [agent-zero-intel](https://apis.io/servers/onchainagentintel-io/agent-zero-intel/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Onchainagentintel Io Openapi Overlay](https://apis.io/overlays/onchainagentintel-io/onchainagentintel-io-openapi-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Onchainagentintel Io Authentication](https://apis.io/security/onchainagentintel-io/onchainagentintel-io-authentication/)
- [Onchainagentintel Io Domain Security](https://apis.io/security/onchainagentintel-io/onchainagentintel-io-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Onchainagentintel Io Plans Pricing](https://apis.io/plans/onchainagentintel-io/onchainagentintel-io-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Onchainagentintel Io Rate Limits](https://apis.io/rate-limits/onchainagentintel-io/onchainagentintel-io-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://onchainagentintel.io/)
- [Documentation](https://onchainagentintel.io/docs)
- [API reference](https://api.onchainagentintel.io/v1/public/docs)
- [Pricing](https://onchainagentintel.io/services)
- [Blog](https://onchainagentintel.io/blog)

## API Evangelist rating

**Kin Score 44.2** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 47.5 |
| Contract governance | 18.2 |
| Operational transparency | 15.8 |
| Developer ergonomics | 50.0 |
| Access clarity | 55.3 |

**Agent readiness 34.4** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | flavored (partial credit) |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 16.7** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/onchainagentintel-io/](https://apis.io/providers/onchainagentintel-io/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Agent Zero: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/onchainagentintel-io/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
