---
name: Collect a payment with Paga
description: Register an NGN payment request and confirm fulfilment via the Paga Collect API.
api: openapi/paga-openapi.yml
operations: [getCollectBanks, requestPayment, checkStatus, refundPaymentV2]
---

# Collect a payment with Paga

Use the **Collect API** (`https://collect.paga.com`, test `https://beta-collect.paga.com`) to request NGN from a payer and confirm the money arrived.

## Auth
HTTP Basic `base64(publicKey:secretKey)` **plus** a `hash` header. The hash is `SHA-512` over an operation-specific ordered concatenation of parameters followed by your account hash key (never transmit the hash key). See `conventions/paga-conventions.yml` and `authentication/paga-authentication.yml`.

## Steps
1. (Optional) Call **`getCollectBanks`** to resolve the payer/payee `bankId` UUIDs.
2. Generate a **unique `referenceNumber`** (max 50 chars) — this is your idempotency key. Call **`requestPayment`** with `amount`, `currency: NGN`, `payer`, and a `callBackUrl`. hash = `SHA-512(referenceNumber + amount + currency + payer.phoneNumber + payer.email + hashKey)`.
3. Wait for the callback (`PAYMENT_COMPLETE` / `PARTIAL_PAYMENT` / `PAYMENT_ERROR` / `PAYMENT_REQUEST_EXPIRED`) on your `callBackUrl`, **and** confirm out-of-band with **`checkStatus`** by `referenceNumber` — do not trust the callback alone.
4. To reverse, call **`refundPaymentV2`** with the `referenceNumber` and optional `refundAmount`.

## Rules
- Re-using a `referenceNumber` is rejected (error `105 Duplicate reference`). Re-send the same reference to `checkStatus`, never to `requestPayment`.
- Amounts are NGN. Errors are integer `statusCode` (see `errors/paga-error-codes.yml`).
