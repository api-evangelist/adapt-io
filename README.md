# adapt-io

Adapt — B2B contact + company data API (250M+ contacts, 12M+ companies, Prospect API v3).

## About

[Adapt](https://www.adapt.io) is a B2B lead intelligence and sales acceleration platform. The
Prospect API exposes search, enrichment, and contact-purchase operations against Adapt's
verified contact and company database via JSON over HTTPS, with header-based authentication
(`email` + `apiKey`) and a 250 requests-per-minute account-level rate limit.

## APIs

- **Adapt Prospect API** (`v3`) — `https://api.adapt.io/v3`
  - `POST /contact/search` — Search Contacts
  - `POST /company/search` — Search Companies
  - `POST /contact/enrich` — Enrich Contact (by email, LinkedIn URL, or firstName + lastName + domain)
  - `POST /contact/fetch` — Purchase Contacts (max 50 ids per request)

## Artifacts

| Folder | Contents |
|---|---|
| [`openapi/`](./openapi) | OpenAPI 3.0 spec for the Prospect API (`adapt-prospect-api-openapi.yml`). |
| [`capabilities/`](./capabilities) | Naftiko capabilities for contact search, company search, enrichment, and purchase. |
| [`json-schema/`](./json-schema) | JSON Schema for Contact and Company entities. |
| [`json-ld/`](./json-ld) | JSON-LD context mapping Adapt entities onto schema.org. |
| [`examples/`](./examples) | Request/response examples for contact search and enrichment. |
| [`vocabulary/`](./vocabulary) | Adapt operational and capability vocabulary. |
| [`plans/`](./plans) | API Commons Plans 0.1 — Free / Starter / Basic / Custom tiers. |
| [`rate-limits/`](./rate-limits) | API Commons Rate Limits 0.1 — 250 rpm account-level + credit quotas. |
| [`finops/`](./finops) | FOCUS-aligned FinOps definition for credit-based metering. |

## Pricing (self-serve)

| Plan | Price | Email credits | Phone credits | Enrich credits | API access |
|---|---|---|---|---|---|
| Free | $0/mo | 25 | — | 25 | No |
| Starter | $49/mo | 500 | — | 500 | No |
| Basic | $99/mo | 1,000 | 100 | 1,000 | No |
| Custom | Contact sales | Negotiated | Negotiated | Negotiated | **Yes** |

API access to the Prospect API is gated to the Custom plan. Annual billing carries a 20%
discount across all tiers.

## Authentication

Every request requires two headers:

```
email:  account-email@your-company.com
apiKey: <key from Adapt account settings>
```

## Rate limits and credits

- 250 requests per minute per account (fixed window).
- `429 APP-429-001` on throttle, with `x-ratelimit-retry-after` indicating wait seconds.
- Credit pools: `search`, `email`, `phone`, `enrich`. Remaining balances are returned on each
  call via `*-remaining-credits` response headers.

## Sources

- <https://www.adapt.io>
- <https://www.adapt.io/api-docs/v3/>
- <https://www.adapt.io/platform/api>
- <https://www.adapt.io/pricing>
- <https://www.adapt.io/our-data>

## Maintainer

Kin Lane — <kin@apievangelist.com>
