---
id: INT-ADDRESS
title: Address validation — contract
type: integration
topic_id: ADDRESS
status: draft
relates_to:
- SD-ADDRESS
---

# Address validation — contract

## Contract status
Integration proposal for agreement. The following fields are the application's logical model, not a copied standard wire-format schema. Verify the provider API version, required fields and enumerations before implementation.

## Reference
[TMF673 Geographic Address](https://github.com/tmforum-apis/TMF673_GeographicAddress)

## Request and correlation
Original address, country, city, street, building and unit. The adapter maps lookup and validation to the agreed TMF673 version.

## Response
Candidates, normalized fields and geographicAddressId for a confirmed result. No candidate and timeout are distinct outcomes.

## Errors, retries and controls
Data validation returns a business error without blind retries. Timeouts and transient failures use bounded retries with backoff. Exceeding the retry limit routes work to a manual handling queue. Requests carry correlationId and a stable deduplication key under the agreed adapter contract. A business data change creates a new operation.

Use managed credentials for server-to-server authorization. Logs contain identifiers and statuses, not secrets. Event processing remembers eventId; older responses do not roll back state.

[Sequence diagram](doc:SEQ-ADDRESS)
