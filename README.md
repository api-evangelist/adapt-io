# Adapt

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

Adapt (adapt.io) is a B2B lead intelligence and sales acceleration platform that provides a database of 250M+ verified business contacts, 16M+ decision makers, and 12M+ company profiles, refreshed at roughly 5M records per day. Adapt sells the data three ways — through a web Prospector for list building and ABM, a LinkedIn/website Chrome extension for in-context contact discovery, and a public REST API for programmatic search, enrichment, and contact purchase. The Prospect API exposes four operations (contact search, company search, contact enrichment, and contact purchase / fetch) with 50+ firmographic, technographic, and demographic attributes per record, header- based authentication via account email + API key, and a 250 requests-per- minute rate limit. Pricing is published for self-serve Free, Starter ($49/mo) and Basic ($99/mo) tiers; API access is gated to the custom enterprise plan with negotiated email, phone, and enrichment credit allotments. Adapt is primarily used by sales, marketing, and RevOps teams for outbound campaigns, CRM enrichment, lead scoring, ICP list building, and data hygiene, with CRM exports to Salesforce, HubSpot, Pipedrive, Zoho, Outreach, and Salesgear.

**Areas:** B2B Data · Contact Data · Company Data · Lead Intelligence · Sales Intelligence · Sales Acceleration · Data Enrichment · Prospecting · Lead Generation · Email Finder · Account Based Marketing · CRM Enrichment

## Adapt on APIs.io

Everything profiled for Adapt is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/adapt-io/](https://apis.io/providers/adapt-io/)** — or go straight to one of the APIs or properties below.

### APIs (4)

- [Adapt Company Search API](https://apis.io/apis/adapt-io/adapt-io-company-search-api/) — Search the company database using firmographic filters.
- [Adapt Contact Enrichment API](https://apis.io/apis/adapt-io/adapt-io-contact-enrichment-api/) — Enrich a known contact with verified email and phone data.
- [Adapt Contact Purchase API](https://apis.io/apis/adapt-io/adapt-io-contact-purchase-api/) — Purchase contacts returned from search to reveal email and phone.
- [Adapt Contact Search API](https://apis.io/apis/adapt-io/adapt-io-contact-search-api/) — Search the contact database using contact and company filters.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [adapt-io-mcp.yml](https://apis.io/servers/adapt-io/adapt-io-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Adapt Io Agentic Access](https://apis.io/agentic-access/adapt-io/adapt-io-agentic-access/)

#### JSON Schema (2)

The data models the API reads and writes.

- [Adapt Company](https://apis.io/schemas/adapt-io/adapt-company/)
- [Adapt Contact](https://apis.io/schemas/adapt-io/adapt-contact/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Adapt Io Context](https://apis.io/jsonld/adapt-io/adapt-io-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Adapt Vocabulary](https://apis.io/vocabularies/adapt-io/adapt-io-vocabulary/)

#### Examples (2)

Example requests and responses.

- [Adapt Contact Enrich Example](https://apis.io/examples/adapt-io/adapt-contact-enrich-example/)
- [Adapt Contact Search Example](https://apis.io/examples/adapt-io/adapt-contact-search-example/)

#### Collections (9)

Postman and Open Collection request collections.

- [Adapt Prospect Company Search API](https://apis.io/collections/adapt-io/open-adapt-io-company-search-api/)
- [Adapt Prospect Company Search Contact Enrichment API](https://apis.io/collections/adapt-io/open-adapt-io-contact-enrichment-api/)
- [Adapt Prospect Company Search Contact Purchase API](https://apis.io/collections/adapt-io/open-adapt-io-contact-purchase-api/)
- [Adapt Prospect Company Search Contact Search API](https://apis.io/collections/adapt-io/open-adapt-io-contact-search-api/)
- [Adapt Prospect API](https://apis.io/collections/adapt-io/open-adapt-prospect-api/)
- [Adapt Prospect Company Search API](https://apis.io/collections/adapt-io/postman-adapt-io-company-search-api/)
- [Adapt Prospect Company Search Contact Enrichment API](https://apis.io/collections/adapt-io/postman-adapt-io-contact-enrichment-api/)
- [Adapt Prospect Company Search Contact Purchase API](https://apis.io/collections/adapt-io/postman-adapt-io-contact-purchase-api/)
- [Adapt Prospect Company Search Contact Search API](https://apis.io/collections/adapt-io/postman-adapt-io-contact-search-api/)

#### Overlays (4)

OpenAPI overlays, including conversational phrasing for each operation.

- [Adapt Io Company Search Api Overlay](https://apis.io/overlays/adapt-io/adapt-io-company-search-api-overlay/)
- [Adapt Io Contact Enrichment Api Overlay](https://apis.io/overlays/adapt-io/adapt-io-contact-enrichment-api-overlay/)
- [Adapt Io Contact Purchase Api Overlay](https://apis.io/overlays/adapt-io/adapt-io-contact-purchase-api-overlay/)
- [Adapt Io Contact Search Api Overlay](https://apis.io/overlays/adapt-io/adapt-io-contact-search-api-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Adapt — jsonschema rules](https://apis.io/rules/adapt-io/adapt-io-jsonschema-spectral-rules/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Adapt Io Authentication](https://apis.io/security/adapt-io/adapt-io-authentication/)
- [Adapt Io Domain Security](https://apis.io/security/adapt-io/adapt-io-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Adapt Io Plans Pricing](https://apis.io/plans/adapt-io/adapt-io-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Adapt Io Rate Limits](https://apis.io/rate-limits/adapt-io/adapt-io-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Adapt Io Finops](https://apis.io/finops/adapt-io/adapt-io-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.adapt.io)
- [Documentation](https://www.adapt.io/api-docs/v3/)
- [Getting started](https://www.adapt.io/api-docs/v3/)
- [API reference](https://www.adapt.io/api-docs/v3/)
- [Pricing](https://www.adapt.io/pricing)
- [Sign up](https://www.adapt.io/free-trial)
- [Support](https://www.adapt.io/contact-us/)
- [Blog](https://www.adapt.io/blog/)
- [Terms of service](https://www.adapt.io/termsAndConditions.htm)
- [Privacy policy](https://www.adapt.io/privacy.htm)

## API Evangelist rating

**Kin Score 53.9** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 66.1 |
| Contract quality | 50.7 |
| Contract governance | 14.4 |
| Operational transparency | 21.1 |
| Developer ergonomics | 63.2 |
| Access clarity | 84.2 |

**Agent readiness 24.3** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | — |

**Regulatory alignment 24.5** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/adapt-io/](https://apis.io/providers/adapt-io/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Adapt: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/adapt-io/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
