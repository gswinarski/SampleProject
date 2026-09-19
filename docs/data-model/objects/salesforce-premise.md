---
id: DATA-PREMISE
title: Premise (proposed) — data model
type: data-object
topic_id: PROJECT
status: draft
relates_to:
- BP-COVERAGE
- SD-COVERAGE
---

# Premise (proposed) — data model

`Premise__c` is a **proposed custom object**, not a Salesforce standard one — there is no out-of-the-box "Premise" object. It holds the aggregated, pre-computed coverage result for one physical address, which is what [Postal-code address lookup and coverage check](doc:TOPIC-COVERAGE) actually reads: a fast lookup against an already-known answer, rather than a live technical qualification call on every check. See [[../README|data model conventions]].

## Proposed (custom) fields

### External_Address_Id__c
Proposed, text (external id, unique). The identifier returned by the postal-code lookup provider for this address — see the [postal-code lookup contract](doc:INT-POSTALLOOKUP). Deliberately the same kind of identifier as the `geographicAddressId` [Address validation and FTTH qualification](doc:SD-ADDRESS) resolves via TMF673; whether the two are reconciled into one identifier is an open decision in [Solution design](doc:SD-COVERAGE).

### Display_Address__c
Proposed, text. The human-readable address text shown back to the customer once resolved — distinct from the transient candidate `displayLabel` the lookup provider returns, which is not persisted.

### Coverage_Status__c
Proposed, picklist (Available / Unavailable / Unknown). The aggregated result [Postal-code address lookup and coverage check](doc:TOPIC-COVERAGE) branches on. This is a cached answer, not a live call — see [[salesforce-premise#Coverage_Last_Refreshed__c]].

### Coverage_Last_Refreshed__c
Proposed, date/time. When [[salesforce-premise#Coverage_Status__c]] was last computed. A value older than the agreed freshness threshold is treated as unknown, triggering the live-qualification hand-off to [Address validation and FTTH qualification](doc:BP-ADDRESS) rather than being trusted.

### Postal_Code__c
Proposed, text. Retained for reporting and to avoid a second postal-code lookup for an address already resolved once.

## Open decisions
How and how often [[salesforce-premise#Coverage_Status__c]] is refreshed — this note describes what the object stores, not the refresh pipeline, which is out of scope for [Postal-code address lookup and coverage check](doc:TOPIC-COVERAGE). Whether [[salesforce-premise#External_Address_Id__c]] is literally the TMF673 `geographicAddressId` or a separate identifier requiring reconciliation.
