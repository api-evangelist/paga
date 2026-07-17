---
name: Set up and charge a direct-debit mandate
description: Tokenize a customer bank account and charge it for one-time or recurring debits.
api: openapi/paga-openapi.yml
operations: [requestPayment, chargeDebitMandate, getChargeMandateStatus, disableMandate]
---

# Set up and charge a direct-debit mandate

The **Direct Debit API** (shares the Collect host `https://collect.paga.com`) tokenizes a customer bank account, then debits it. **Money-movement — gate behind human approval.**

## Auth
HTTP Basic + `hash` header (see `conventions/paga-conventions.yml`).

## Steps
1. Initiate mandate tokenization via **`requestPayment`** (the Direct Debit flow reuses `/paymentRequest`); the customer approves the mandate against their bank account, keyed by your `accountReference`.
2. Once approved, debit with **`chargeDebitMandate`** using a unique `referenceNumber`, `amount`, and the `accountReference`. hash = `SHA-512(referenceNumber + amount + accountReference + hashKey)`.
3. Confirm each charge with **`getChargeMandateStatus`** by `referenceNumber`.
4. Revoke the mandate with **`disableMandate`** (`referenceNumber` + `accountReference`).

## Rules
- `accountReference` identifies the mandate across charges; `referenceNumber` is unique per charge (idempotency; duplicate → error `105`).
- Only charge an approved mandate; a disabled mandate cannot be charged.
