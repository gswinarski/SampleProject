---
id: INT-TICKET
title: Submit an issue to OSS — contract
type: integration
topic_id: ISSUE
status: draft
relates_to:
- SD-ISSUE
---

# Submit an issue to OSS — contract

## Contract status
Integration proposal for agreement. The following fields are the application's logical model, not a copied standard wire-format schema. Verify the provider API version, required fields and enumerations before implementation.

## Reference
[TMF621 Trouble Ticket](https://www.tmforum.org/resources/standard/tmf621-trouble-ticket-management-api-rest-specification-r19-0-0/)

## Request and correlation
CaseId, service reference, symptoms, category, priority and onset time. The adapter maps these to the provider’s TMF621 contract. CaseId plus operation version provides deduplication.

## Response
externalTicketId, technical status, update time and a widespread incident reference if applicable. Callback events update the Case; technical closure remains separate from the customer decision.

## Errors, retries and controls
Data validation returns a business error without blind retries. Timeouts and transient failures use bounded retries with backoff. Exceeding the retry limit routes work to a manual handling queue. Requests carry correlationId and a stable deduplication key under the agreed adapter contract. A business data change creates a new operation.

Use managed credentials for server-to-server authorization. Logs contain identifiers and statuses, not secrets. Event processing remembers eventId; older responses do not roll back state.

[Sequence diagram](doc:SEQ-TICKET)
