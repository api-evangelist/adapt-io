# Adapt (adapt-io)

Adapt (adapt.io) is a B2B lead intelligence and sales acceleration platform that provides a database of 250M+ verified business contacts, 16M+ decision makers, and 12M+ company profiles, refreshed at roughly 5M records per day. Adapt sells the data three ways — through a web Prospector for list building and ABM, a LinkedIn/website Chrome extension for in-context contact discovery, and a public REST API for programmatic search, enrichment, and contact purchase. The Prospect API exposes four operations (contact search, company search, contact enrichment, and contact purchase / fetch) with 50+ firmographic, technographic, and demographic attributes per record, header- based authentication via account email + API key, and a 250 requests-per- minute rate limit. Pricing is published for self-serve Free, Starter ($49/mo) and Basic ($99/mo) tiers; API access is gated to the custom enterprise plan with negotiated email, phone, and enrichment credit allotments. Adapt is primarily used by sales, marketing, and RevOps teams for outbound campaigns, CRM enrichment, lead scoring, ICP list building, and data hygiene, with CRM exports to Salesforce, HubSpot, Pipedrive, Zoho, Outreach, and Salesgear.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/adapt-io/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/adapt-io/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Provider
- **Access:** 3rd-Party

## Tags

- B2B Data
- Contact Data
- Company Data
- Lead Intelligence
- Sales Intelligence
- Sales Acceleration
- Data Enrichment
- Prospecting
- Lead Generation
- Email Finder
- ABM
- CRM Enrichment
- Marketing
- Sales

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Adapt Prospect API

REST API for searching Adapt's B2B contact and company database, enriching known contacts by email/LinkedIn/name+domain, and purchasing contacts to reveal verified email addresses and phone numbers. JSON over HTTPS with header-based authentication (email + apiKey). Default rate limit of 250 requests per minute per account; pagination via cursorMark; credit consumption surfaced through `x-call-credit-type` and `*-remaining-credits` response headers.

- **Human URL:** [https://www.adapt.io/api-docs/v3/](https://www.adapt.io/api-docs/v3/)
- **Base URL:** `https://api.adapt.io/v3`

#### Tags

- Contacts
- Companies
- Enrichment
- Search
- B2B Data

#### Properties

- [Documentation](https://www.adapt.io/api-docs/v3/)
- [Documentation](https://www.adapt.io/platform/api)
- [OpenAPI](openapi/adapt-prospect-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/adapt-prospect-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/adapt-prospect-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/adapt-contact-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/adapt-company-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/adapt-io-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Examples](examples/adapt-contact-search-example.json)
- [Examples](examples/adapt-contact-enrich-example.json)

## Common Properties

- [Website](https://www.adapt.io)
- [Portal](https://www.adapt.io/platform/api)
- [Documentation](https://www.adapt.io/api-docs/v3/)
- [Getting Started](https://www.adapt.io/api-docs/v3/)
- [Sign Up](https://app.adapt.io/users/sign_up)
- [Login](https://app.adapt.io/users/sign_in)
- [Pricing](https://www.adapt.io/pricing)
- [Plans](plans/adapt-io-plans-pricing.yml)
- [Rate Limits](rate-limits/adapt-io-rate-limits.yml)
- [Fin Ops](finops/adapt-io-finops.yml)
- [Product](https://www.adapt.io/platform/prospecting)
- [Product](https://www.adapt.io/platform/api)
- [Product](https://www.adapt.io/data-os)
- [Product](https://www.adapt.io/our-data)
- [Extension](https://chromewebstore.google.com/detail/adapt-prospector/lkfklokpfbpcmpdacencdkjncpojdgff)
- [Directory](https://www.adapt.io/directory/industry)
- [Blog](https://blog.adapt.io)
- [Company](https://www.adapt.io/about-us)
- [Customers](https://www.adapt.io/customers)
- [Contact Us](https://www.adapt.io/contact-us)
- [Privacy Policy](https://www.adapt.io/privacy-policy)
- [Terms of Service](https://www.adapt.io/terms-of-service)
- [LinkedIn](https://www.linkedin.com/company/adapt-io)
- [Twitter](https://twitter.com/adapt_io)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
