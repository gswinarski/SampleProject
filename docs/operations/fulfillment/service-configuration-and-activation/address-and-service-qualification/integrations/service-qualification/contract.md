---
id: INT-QUALIFICATION
title: FTTH qualification — contract
type: integration
topic_id: ADDRESS
status: draft
relates_to:
- SD-ADDRESS
---

# FTTH qualification — contract

## Contract status
Integration proposal for agreement. The following fields are the application's logical model, not a copied standard wire-format schema. Verify the provider API version, required fields and enumerations before implementation.

## Reference
[TMF645 Service Qualification](https://github.com/tmforum-apis/TMF645_ServiceQualification)

## Request and correlation
Verified geographicAddressId, unit, FTTH service type/specification and requestCorrelationId. Qualification is neither an order nor a reservation.

## Response
qualificationId, available/unavailable/pending/unknown in the application model, reason and checkedAt. The adapter maps provider enumerations. An older response must not overwrite a newer address.

## Errors, retries and controls
Data validation returns a business error without blind retries. Timeouts and transient failures use bounded retries with backoff. Exceeding the retry limit routes work to a manual handling queue. Requests carry correlationId and a stable deduplication key under the agreed adapter contract. A business data change creates a new operation.

Use managed credentials for server-to-server authorization. Logs contain identifiers and statuses, not secrets. Event processing remembers eventId; older responses do not roll back state.

[Sequence diagram](doc:SEQ-QUALIFICATION)
