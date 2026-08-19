---
name: adapt-io-build-and-purchase-prospect-list
description: >-
  Build a targeted B2B prospect list from Adapt's contact database and purchase the
  contactable records, paging with cursorMark and watching credit balances so the run
  cannot overspend.
api: adapt-io:adapt-io-contact-search-api
apis:
  - adapt-io:adapt-io-contact-search-api
  - adapt-io:adapt-io-contact-purchase-api
operations:
  - searchContacts
  - purchaseContacts
generated: '2026-08-13'
method: generated
source: https://www.adapt.io/api-docs/v3/
---

# Build and purchase a prospect list (Adapt)

Search returns identity without contactability. Purchase reveals email and phone and
spends credits. Never merge the two steps blindly — search is cheap, purchase is not.

## Preconditions

- An Adapt **Custom (enterprise)** plan. Free, Starter and Basic tiers do not issue
  Prospect API credentials — a lesser plan fails with `APP-403-002`.
- Two headers on every request, sent together:
  - `email` — the account's registered email address
  - `apiKey` — from https://leads.adapt.io/profile/settings
- Filter values for `city`, `state`, `country`, `companyIndustry`, `companySubIndustry`
  and `technology` must match Adapt's reference sheets **exactly and case-sensitively**
  (see `data-model/adapt-io-data-model.yml`). An unrecognized value silently returns
  nothing rather than erroring.

## Step 1 — Search contacts (`searchContacts`)

`POST https://api.adapt.io/v3/contact/search`

Compose the ICP from contact filters (`title`, `excludeTitle`, `titleExactMatch`,
`level`, `department`) and company filters (`companyDomain`, `companyName`,
`companyKeyword`, `companyHeadCount`, `companyRevenue`, `companyIndustry`,
`companySubIndustry`, `technology`, `city`, `state`, `country`).

Set these deliberately:

- `required: ["EMAIL"]` — return only contacts that actually have an email. This is the
  default; keep it unless you want unreachable records in the list.
- `minimumEmailDeliverabilityScore: 95` — highest confidence. 85 is medium, 75 is low.
- `dontDisplayOwnedContact: true` — exclude contacts you already bought. **This is the
  single most important flag in the workflow**: without it a re-run re-purchases records
  you already own and spends credits twice.
- `maxContactPerCompany` — 1, 2 or 3. Caps concentration in a single account.
- `limit` — records per call.
- `locationPreference` — `contact`, `company`, `*` (default) or `AND`.

Read the response as `{message, code, data[], cursorMark, totalResults}`.

**Check `code` before anything else.** `APP-200-001` is a hit; `APP-200-002` means no
results found and still arrives with HTTP 200. Branching on HTTP status alone will treat
an empty list as a success.

Note `totalResults` and the credit headers `x-call-credit-type` and
`search-remaining-credits`.

## Step 2 — Page with `cursorMark`

Pass the `cursorMark` from the previous response into the next request body, keeping all
other filters identical. Stop when you have `totalResults` records, when `data` is
empty, or when you reach your own cap. There is no documented cursor expiry — do not
park a cursor for a later session.

Collect each record's `id`. That id is the only token that purchases the contact.

## Step 3 — Decide before you spend

Purchase is irreversible and there is no idempotency key. Before calling step 4:

- Deduplicate the id list.
- Subtract ids you already own.
- Compare the count against `email-remaining-credits` and `phone-remaining-credits`
  from your last purchase response, or against the plan allotment in
  `plans/adapt-io-plans-pricing.yml`.
- **Surface the count and the credit cost to a human and get confirmation.** This is the
  human-in-the-loop point for the whole workflow.

## Step 4 — Purchase (`purchaseContacts`)

`POST https://api.adapt.io/v3/contact/fetch`

```json
{ "contactIds": ["5c05fc5d4a381d0242943e02"] }
```

- Maximum **50 ids per request**. Exceeding it returns `APP-400-002`. Chunk accordingly.
- Response `data[]` carries the same contact records plus `email`, and `phoneNumber[]`
  entries typed `direct_line`, `mobile_number` or `other`.
- Read `email-remaining-credits` and `phone-remaining-credits` from the response headers
  after every chunk and stop the run when either lane approaches zero.

## Step 5 — Handle failures correctly

The distinction that matters most: **429 is throughput, 403 is money.**

| Code | Meaning | Do |
| --- | --- | --- |
| `APP-429-001` (429) | 250 req/min exceeded | Sleep `x-ratelimit-retry-after` seconds, retry the same chunk |
| `APP-403-003` (403) | Out of credits | **Stop.** Retrying never succeeds. Escalate to a human |
| `APP-403-002` (403) | Plan has no API access | Stop. Needs a Custom plan |
| `APP-401-001` (401) | Bad email/apiKey pair | Stop. Both headers are required |
| `APP-400-002` (400) | More than 50 contactIds | Re-chunk and retry |
| `APP-500-001` (500) | Adapt server error | Exponential backoff. **Before retrying a purchase chunk, re-check ownership** — a timed-out call may already have spent credits |

Full catalog: `errors/adapt-io-problem-types.yml`.

## Notes

- Account-level suppression lists (uploaded at
  https://leads.adapt.io/profile/suppression-list) silently filter API results. Two
  accounts running the same query can get different lists.
- `companyIndustry` and `companySubIndustry` are OR-ed. Supplying both an industry and
  its sub-industry **widens** the result, because industry is the superset.
- Rate limit increases: success@adapt.io.
