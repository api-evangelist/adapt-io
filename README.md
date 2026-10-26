# Adapt (adapt-io)

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
