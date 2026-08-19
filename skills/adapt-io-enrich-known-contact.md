---
name: adapt-io-enrich-known-contact
description: >-
  Enrich a partially-known contact — a lead-form submission, a CRM record, a LinkedIn
  URL — into a full Adapt profile with verified email and direct-dial phone, choosing
  the right input combination and falling back cleanly when no match is found.
api: adapt-io:adapt-io-contact-enrichment-api
apis:
  - adapt-io:adapt-io-contact-enrichment-api
operations:
  - enrichContact
generated: '2026-08-13'
method: generated
source: https://www.adapt.io/api-docs/v3/
---

# Enrich a known contact (Adapt)

One contact in, one contact out. This is the CRM-hygiene and lead-form path — not the
list-building path (see `adapt-io-build-and-purchase-prospect-list`).

## Preconditions

- Adapt **Custom (enterprise)** plan; headers `email` and `apiKey` on every request.
- Enrichment draws on the **enrichment** credit lane, separate from search, email and
  phone credits.

## Step 1 — Pick an input combination

`POST https://api.adapt.io/v3/contact/enrich`

Adapt matches on exactly one of three combinations. Choose in this order of confidence:

1. `email` — the contact's email address. Strongest key.
2. `linkedinURL` — e.g. `linkedin.com/in/mindofkira`.
3. `firstName` **AND** `lastName` **AND** `domain` — all three are required together;
   a partial name triple will not match.

Sending a combination that is not one of these three returns `APP-400-001`.

## Step 2 — Opt into the billable fields

`include` is an array and it defaults to empty, which returns the profile **without**
email or phone:

```json
{
  "email": "gautam@adapt.io",
  "include": ["EMAIL", "PHONE"]
}
```

- `["EMAIL"]` — response carries the email address
- `["PHONE"]` — response carries the mobile number
- `["EMAIL","PHONE"]` — both
- omitted or `[]` — neither

Request only the lanes you need. Each is metered.

## Step 3 — Read the response

`{message, code, data}` — here `data` is a single **object**, not an array. This differs
from search and purchase, which return `data` as an array. A client that assumes an
array will break on this operation.

Useful fields on the returned contact: `id`, `firstName`, `lastName`, `title`,
`department[]`, `level`, `city`/`state`/`country`, `linkedin`, `twitter`, `facebook`,
`emailDeliverabilityScore`, and an embedded `company` object with firmographics
(`industry`, `subIndustry[]`, `headCount`, `revenue`, HQ address, `phoneNumber[]`).

Gate downstream use on `emailDeliverabilityScore`: **95 high, 85 medium, 75 low**. Do not
route an 75-scored address into a cold-send sequence.

Read `x-call-credit-type` and `enrich-remaining-credits` from the response headers to
track budget.

## Step 4 — Fall back on a miss

`APP-200-002` — "Requested information about the contact not found" — arrives with
**HTTP 200**. Treat it as a miss, not a success:

1. Retry once with a different input combination (e.g. `linkedinURL` if `email` missed).
2. If still unmatched, fall back to `searchContacts` with `companyDomain` plus `title`
   or `level` to find an alternate contact at the same account.
3. Record the miss. Do not loop — a miss is deterministic for the same input.

## Errors

| Code | Meaning | Do |
| --- | --- | --- |
| `APP-200-002` (200) | No match | Try another input combination, then stop |
| `APP-400-001` (400) | Invalid request / no valid input combination | Fix the payload |
| `APP-401-001` (401) | Invalid email or apiKey | Stop |
| `APP-403-003` (403) | Out of enrichment credits | **Stop.** Retry never succeeds |
| `APP-429-001` (429) | 250 req/min exceeded | Sleep `x-ratelimit-retry-after`, retry |
| `APP-500-001` (500) | Server error | Exponential backoff |

Full catalog: `errors/adapt-io-problem-types.yml`.

## Batching note

There is no bulk enrichment endpoint. Enriching a CRM list means one call per record
against a 250 req/min ceiling — roughly 15,000 records per hour at best, before credit
limits bite. Plan long-running jobs around the credit allotment, not the rate limit.
