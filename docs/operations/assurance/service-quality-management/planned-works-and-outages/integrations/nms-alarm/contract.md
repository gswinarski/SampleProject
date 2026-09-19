---
id: INT-NMS
title: NMS alarm/event ingestion — contract
type: integration
topic_id: OUTAGE
status: draft
relates_to:
- SD-OUTAGE
---

# NMS alarm/event ingestion — contract

## Contract status
Integration proposal for agreement. The following fields are the application's logical model, not a copied standard wire-format schema. Verify the provider API version, required fields and enumerations before implementation.

## Reference
[TMF642 Alarm Management](https://github.com/tmforum-apis/TMF642_AlarmManagement)

## Request and correlation
The NMS pushes an event carrying a stable networkEventId, one or more affected network service identifiers, eventType (planned work, outage, cleared), severity/impact, and either a planned start/end window or a detection time. networkEventId is the deduplication key: a resent event updates the same Incident.

## Response
Salesforce acknowledges receipt. There is no synchronous availability decision in this contract — correlation to Assets and Incident creation/update happen after acknowledgement, asynchronously from the NMS's perspective.

## Errors, retries and controls
Data validation returns a business error without blind retries. Timeouts and transient failures use bounded retries with backoff. Exceeding the retry limit routes work to a manual handling queue. Requests carry correlationId and a stable deduplication key under the agreed adapter contract. A business data change creates a new operation.

Use managed credentials for server-to-server authorization. Logs contain identifiers and statuses, not secrets. Event processing remembers eventId; older responses do not roll back state.

[Sequence diagram](doc:SEQ-NMS)
