---
id: INT-BILL
title: Billing adjustment request — contract
type: integration
topic_id: BILL
status: draft
relates_to:
- SD-BILL
---

# Billing adjustment request — contract

## Contract status
Integration proposal for agreement. The following fields are the application's logical model, not a copied standard wire-format schema. Verify the provider API version, required fields and enumerations before implementation.

## Reference
Operator-specific project contract; no TMF621 implementation or standard adjustment API is claimed.

## Request and correlation
CaseId, invoiceId, invoiceItemId, approved amount and currency, reason, approver and businessRequestId. Billing verifies authorization and consistency with the original charge.

## Response
adjustmentId and accepted/confirmed/rejected state. Only a confirmed adjustment permits telling the customer it has been applied.

## Errors, retries and controls
Data validation returns a business error without blind retries. Timeouts and transient failures use bounded retries with backoff. Exceeding the retry limit routes work to a manual handling queue. Requests carry correlationId and a stable deduplication key under the agreed adapter contract. A business data change creates a new operation.

Use managed credentials for server-to-server authorization. Logs contain identifiers and statuses, not secrets. Event processing remembers eventId; older responses do not roll back state.

[Sequence diagram](doc:SEQ-BILL)
