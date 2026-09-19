---
id: SD-COVERAGE
title: Postal-code address lookup and coverage check — solution design
type: solution-design
topic_id: COVERAGE
status: draft
relates_to:
- BP-COVERAGE
- AC-COVERAGE
---

# Postal-code address lookup and coverage check — solution design

## Component responsibilities
| Component | Proposed responsibility | Confirm in the target org |
|---|---|---|
| Experience Cloud order-capture page | Postal code entry, candidate list, coverage result, Lead capture form | Guest vs. authenticated access; whether this page is public |
| Postal-code lookup adapter | Calls the external, currently unspecified provider and maps its response to the application's logical model | Provider selection, rate limits, response caching |
| Integration Procedures | Request/response shaping between the portal and the adapter | OmniStudio runtime and Named Credentials |
| Premise | Aggregated, pre-computed coverage per address; the record this process actually reads | How and how often the aggregate is refreshed (out of scope here) |
| Lead | Captures an out-of-coverage prospect for later follow-up | Lead assignment rules and how/when it is converted |
| Flow | Coverage decision routing (available / unavailable / unknown-stale) | Freshness threshold value |

## High-level flow (component view)
1. Portal → Postal-code lookup adapter: postal code.
2. Adapter → external provider: postal code; provider → adapter: candidate list (external address id + display label).
3. Portal: customer selects one candidate.
4. Portal → Salesforce: resolve or create [[salesforce-premise]] by the candidate's external address id.
5. Salesforce reads [[salesforce-premise#Coverage_Status__c]] and [[salesforce-premise#Coverage_Last_Refreshed__c]].
6. Branch on the result: confirm coverage; create a [[salesforce-lead]]; or hand off to [Address validation and FTTH qualification](doc:BP-ADDRESS) when the aggregate is missing or stale.

## Data model
This process reads and writes [[salesforce-premise]] — the object holding the aggregated availability result for an address — most directly [[salesforce-premise#External_Address_Id__c]], [[salesforce-premise#Coverage_Status__c]], [[salesforce-premise#Coverage_Last_Refreshed__c]] and [[salesforce-premise#Display_Address__c]]. An out-of-coverage result is captured on [[salesforce-lead]], specifically [[salesforce-lead#Street]], [[salesforce-lead#PostalCode]], [[salesforce-lead#LeadSource]] and the proposed [[salesforce-lead#Requested_Premise__c]]. See those notes for full field definitions and standard-vs-proposed status; this document does not repeat it.

[[salesforce-premise#External_Address_Id__c]] is deliberately the same kind of identifier as the `geographicAddressId` [Address validation and FTTH qualification](doc:SD-ADDRESS) resolves via TMF673 — whether they are literally the same value from the same registry, or two identifiers that need reconciling, is an open decision below.

## Event handling
Resolving a candidate to a Premise is an upsert keyed on [[salesforce-premise#External_Address_Id__c]], never on the free-text display label — two different postal-code lookups for the same physical address must land on the same Premise. A Lead is only created once per address+contact while the address remains unavailable; a repeat check reuses the existing Lead rather than creating another.

## Security and observability
The postal-code lookup provider never receives customer identity, only the postal code. The portal never calls the live technical qualification integration directly — that hand-off, if triggered, goes through [Address validation and FTTH qualification](doc:SD-ADDRESS) under its own rules.

## Open decisions
Who the postal-code-to-address provider actually is, and its response shape and limits; the freshness threshold for [[salesforce-premise#Coverage_Last_Refreshed__c]]; whether [[salesforce-premise#External_Address_Id__c]] is reconciled with TMF673's `geographicAddressId` or kept as a separate identifier; how and how often [[salesforce-premise]] coverage aggregates are refreshed; Lead assignment and follow-up ownership once out-of-coverage volume grows.
