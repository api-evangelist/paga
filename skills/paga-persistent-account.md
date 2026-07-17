---
name: Issue a persistent payment account
description: Create and manage a reusable NUBAN account number for a customer to collect payments any time.
api: openapi/paga-openapi.yml
operations: [registerPersistentPaymentAccount, getPersistentPaymentAccount, updatePersistentPaymentAccount, deletePersistentPaymentAccount]
---

# Issue a persistent payment account

A persistent payment account is a reusable NUBAN number tied to a customer so your organization can receive bank/Paga transfers at any time (Collect API).

## Auth
HTTP Basic + `hash` header (see `conventions/paga-conventions.yml`).

## Steps
1. Call **`registerPersistentPaymentAccount`** with a unique `referenceNumber`, `accountName`, `phoneNumber`, a client `accountReference`, and optionally `financialIdentificationNumber` (BVN) and a `callbackUrl`. The response returns the assigned NUBAN.
2. Retrieve details any time with **`getPersistentPaymentAccount`** (`referenceNumber` + `accountReference`).
3. Change mutable properties (not the NUBAN or `accountReference`) with **`updatePersistentPaymentAccount`**.
4. Remove the identifier with **`deletePersistentPaymentAccount`** — this is irreversible.

## Rules
- `accountReference` is your stable key for the account; `referenceNumber` stays unique per call (idempotency; duplicates → error `105`).
- Incoming payments to the NUBAN trigger the Collect callback events (`asyncapi/paga-webhooks.yml`).
