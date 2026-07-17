---
name: Disburse funds with the Paga Business API
description: Validate a recipient and send money to a bank account or phone number from your business Paga account.
api: openapi/paga-openapi.yml
operations: [getBusinessBanks, validateDepositToBank, depositToBank, moneyTransfer, getOperationStatus, accountBalance]
---

# Disburse funds with the Paga Business API

Use the **Business API** (`https://www.mypaga.com`, test `https://beta.mypaga.com`) to pay out to banks and wallets. **Money-movement — gate behind human approval** (`agentic-access/paga-agentic-access.yml`).

## Auth
`principal` + `credentials` + `hash` headers. **Caller IP must be whitelisted.** hash example (deposit) = `SHA-512(referenceNumber + amount + destinationBankUUID + destinationBankAccountNumber + hashKey)`.

## Steps
1. (Optional) Check funds with **`accountBalance`** and resolve bank UUIDs with **`getBusinessBanks`**.
2. For a bank payout, call **`validateDepositToBank`** (name enquiry) to confirm the account name before debiting.
3. Send with **`depositToBank`** (to a bank account) or **`moneyTransfer`** (to a phone/bank) using a unique `referenceNumber`.
4. Confirm with **`getOperationStatus`** by `referenceNumber`.

## Rules
- Unique `referenceNumber` per payout (idempotency; duplicate → error `105`). `139` = Insufficient Balance, `107` = Invalid Recipient Account (`errors/paga-error-codes.yml`).
- Never re-issue a payout on timeout — query `getOperationStatus` first.
