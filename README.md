# Paga (paga)

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

Paga (Pagatech Financial Services Limited) is a Nigerian mobile-money and payments company founded in 2009 and licensed by the Central Bank of Nigeria. Its developer platform exposes REST APIs — the Business API, Collect API, and Direct Debit API — for disbursements, airtime/data and bill payments, bank deposits, and NGN collections via payment requests and persistent (NUBAN) account numbers. Authentication combines a principal/credential key pair with a per-request SHA-512 hash header.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/paga/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/paga/refs/heads/main/apis.yml)

## Tags

- Payments
- Mobile Money
- Fintech
- Collections
- Nigeria

## Timestamps

- **Created:** 2026-07-17
- **Modified:** 2026-07-17

## APIs

### Paga Collect API

Collect NGN payments from customers via payment requests (bank transfer, USSD, card, agent, or Paga wallet) and persistent NUBAN account numbers, with status checks, history, and refunds. HTTP Basic auth plus a per-operation SHA-512 hash header.

- **Human URL:** [https://developer-docs.paga.com/docs/paga-collect-api](https://developer-docs.paga.com/docs/paga-collect-api)
- **Base URL:** `https://collect.paga.com`

#### Tags

- Collections
- Payments
- Persistent Payment Account

#### Properties

- [Documentation](https://developer-docs.paga.com/docs/paga-collect-api)
- [API Reference](https://developer-docs.paga.com/docs/operations-1)
- [OpenAPI](openapi/paga-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/paga.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Paga Business API

Integrate the Paga platform for money transfers, airtime/data purchase, merchant and bill payments, bank deposits, account balance, transaction history, and customer onboarding. `principal`/`credentials` header auth plus a per-operation SHA-512 hash header; requires IP whitelisting.

- **Human URL:** [https://developer-docs.paga.com/docs/business-rest-api](https://developer-docs.paga.com/docs/business-rest-api)
- **Base URL:** `https://www.mypaga.com/paga-webservices/business-rest/secured`

#### Tags

- Disbursements
- Airtime
- Merchant Payment

#### Properties

- [Documentation](https://developer-docs.paga.com/docs/business-rest-api)
- [API Reference](https://developer-docs.paga.com/docs/business-rest-api-operations)
- [OpenAPI](openapi/paga-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/paga.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Paga Direct Debit API

Tokenize a customer bank account (mandate) and charge it for one-time or recurring debits, with mandate status checks and revocation. Shares the Collect API host and HTTP Basic + SHA-512 hash auth.

- **Human URL:** [https://developer-docs.paga.com/docs/direct-debit-api](https://developer-docs.paga.com/docs/direct-debit-api)
- **Base URL:** `https://collect.paga.com`

#### Tags

- Direct Debit
- Mandate
- Tokenization

#### Properties

- [Documentation](https://developer-docs.paga.com/docs/direct-debit-api)
- [OpenAPI](openapi/paga-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/paga.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)

### Paga Connect

OAuth-based hosted checkout that lets third parties charge a customer's Paga wallet and read account/merchant details after the customer authorizes access. Documented separately from the hash-authenticated REST surfaces.

- **Human URL:** [https://developer-docs.paga.com/docs/paga-connect](https://developer-docs.paga.com/docs/paga-connect)
- **Base URL:** `https://www.mypaga.com`

#### Tags

- OAuth
- Checkout
- Payments

#### Properties

- [Documentation](https://developer-docs.paga.com/docs/paga-connect)

## Common Properties

- [Agentic Access](agentic-access/paga-agentic-access.yml)
- [Trust Center](security/paga-trust-center.yml)
- [Vulnerability Disclosure](security/paga-vulnerability-disclosure.yml)
- [Domain Security](security/paga-domain-security.yml)
- [Authentication](authentication/paga-authentication.yml)
- [GitHub Organization](https://github.com/Paga-Developer-Community)
- [LinkedIn](https://www.linkedin.com/company/paga-tech)
- [Website](https://www.paga.com/)
- [Documentation](https://developer-docs.paga.com/)
- [Plans](plans/paga-plans-pricing.yml)
- [Rate Limits](rate-limits/paga-rate-limits.yml)
- [Fin Ops](finops/paga-finops.yml)

## Authentication

Paga issues three secrets from the Business Account dashboard (Developer Tools → API keys), with separate test and live sets:

- **principal** — public key / merchant public ID
- **credentials** — secret key / password
- **hash key** — HMAC key used to build the per-request `hash` header

Every operation carries a `hash` header: `SHA-512(<ordered operation parameters> + hashKey)`, concatenated with no separators. The Collect and Direct Debit APIs wrap the principal/credential pair in HTTP Basic (`base64(publicKey:secretKey)`); the Business API sends them as `principal` and `credentials` headers and additionally requires the caller's IP to be whitelisted. All amounts are in Nigerian Naira (NGN).

## WebSocket Review

Paga does **not** expose a documented public WebSocket API. All product surfaces are synchronous HTTPS REST; asynchronous events are delivered as outbound HTTP webhook callbacks to a merchant `callbackUrl`. See [review.yml](review.yml).

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
