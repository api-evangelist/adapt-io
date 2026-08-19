---
name: adapt-io-account-research-and-sizing
description: >-
  Size a target market with Adapt's company database — find the accounts that match an
  ICP, read how many contacts Adapt holds for each, and decide where to spend contact
  credits before spending any.
api: adapt-io:adapt-io-company-search-api
apis:
  - adapt-io:adapt-io-company-search-api
  - adapt-io:adapt-io-contact-search-api
operations:
  - searchCompanies
  - searchContacts
generated: '2026-08-13'
method: generated
source: https://www.adapt.io/api-docs/v3/
---

# Account research and market sizing (Adapt)

Company search is the cheapest way to test an ICP hypothesis before committing contact
credits. `numberOfContacts` tells you how deep Adapt's coverage goes per account, so you
can rank accounts by reachability rather than guessing.

## Preconditions

- Adapt **Custom (enterprise)** plan; headers `email` and `apiKey` on every request.
- Company search consumes the **search** credit lane.

## Step 1 — Define the account ICP (`searchCompanies`)

`POST https://api.adapt.io/v3/company/search`

```json
{
  "country": ["United States"],
  "subIndustry": ["Internet"],
  "limit": 50
}
```

Available filters: `name[]`, `domain[]`, `headCount[]`, `revenue[]`, `industry[]`,
`subIndustry[]`, `city[]`, `state[]`, `country[]`, `limit`, `cursorMark`.

Use the published banded values verbatim:

- `headCount`: `0 - 25`, `25 - 100`, `100 - 250`, `250 - 1000`, `1K - 10K`,
  `10K - 50K`, `50K - 100K`, `> 100K`
- `revenue`: `$0 - 1M`, `$1 - 10M`, `$10 - 50M`, `$50 - 100M`, `$100 - 250M`,
  `$250 - 500M`, `$500M - 1B`, `> $1B`

Two rules that decide whether the query works at all:

- **Filter on sub-industry alone if you want a narrow result.** Supplying both
  `industry` and `subIndustry` returns everything in the industry, because industry is
  the superset. This widens rather than narrows.
- **`city`, `state` and `country` are case-sensitive exact matches** against Adapt's
  location reference sheet. A near-miss returns nothing, not an error.

## Step 2 — Read the size signal

The response is `{message, code, data[], cursorMark, totalResults}`.

- `totalResults` — the size of the addressable account universe under this ICP. This is
  the number to iterate on when tuning the hypothesis.
- Per company: `name`, `website`, `street`/`city`/`state`/`country`/`zipcode`,
  `phoneNumber[]` (typed `company_line`), `linkedin`, `twitter`, `facebook`, `industry`,
  `subIndustry[]`, `headCount`, `revenue`, and **`numberOfContacts`**.

`numberOfContacts` is the coverage depth Adapt holds for that account. Rank targets by
it: an account with 66 known contacts is workable, one with 2 is not, regardless of how
well it fits the firmographic profile.

Check `code` first — `APP-200-002` means no results found and still returns HTTP 200.

## Step 3 — Page the account list

Echo `cursorMark` into the next call with identical filters. Track
`search-remaining-credits` from the response headers as you go.

## Step 4 — Drill into the accounts worth pursuing

For the shortlist, call `searchContacts` with `companyDomain: [ ... ]` plus the buying
roles you want (`level: ["C-Level","VP-Level"]`, `department: ["Sales"]`, or `title[]`
with `titleExactMatch: true`). Set `maxContactPerCompany` to 1–3 to keep the list even
across accounts.

Nothing is purchased at this point — contact search returns identity without email or
phone. Hand the ranked list to `adapt-io-build-and-purchase-prospect-list` when the ICP
is settled.

## Notes

- There is no "list contacts at this company" operation. The traversal from company to
  contacts is done client-side by feeding `website`/`domain` into `searchContacts` as
  `companyDomain`.
- Companies carry **no stable id** — only domain/website. Join Adapt companies to your
  CRM on normalized domain.
- Domain suppression lists uploaded at https://leads.adapt.io/profile/suppression-list
  silently remove companies from results, so a sizing number is account-specific.
- Errors follow the standard catalog: `errors/adapt-io-problem-types.yml`.
