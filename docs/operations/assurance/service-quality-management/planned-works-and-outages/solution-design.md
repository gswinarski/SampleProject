---
id: SD-OUTAGE
title: Planned works and mass outage notification — solution design
type: solution-design
topic_id: OUTAGE
status: draft
relates_to:
- BP-OUTAGE
- AC-OUTAGE
---

# Planned works and mass outage notification — solution design

## Component responsibilities
| Component | Proposed responsibility | Confirm in the target org |
|---|---|---|
| Alarm ingestion adapter | Receives the NMS event and maps it to the application's logical model | Whether the target NMS actually exposes a TMF642-shaped API or a proprietary one |
| Incident | Standard Customer Service Incident Management object: groups an affected condition, its window and status | Whether Incident Management is enabled and its entitlement/milestone features are needed here |
| Asset | Represents a customer's service; carries the network identifier used to correlate an NMS event | Confirm this is the object used for the customer/service relationship in the target org |
| Incident–Asset link | Records which Assets an Incident affects | Whether a dedicated junction object is used or a different standard relationship |
| Experience Cloud home page component | Reads open, customer-visible Incidents linked to the logged-in customer's Assets and renders the banner | Component reuse vs. a purpose-built one; caching/refresh interval |
| Flow / integration layer | Idempotency and correlation for repeated NMS events | Replay window and the identifier used for deduplication |

## Data model
This process reads and writes [[salesforce-incident]] and [[salesforce-asset]], most directly [[salesforce-incident#Category]], [[salesforce-incident#StartDateTime]], [[salesforce-incident#EndDateTime]], [[salesforce-incident#DetectedDateTime]], [[salesforce-incident#Impact]], [[salesforce-incident#IsMajorIncident]], [[salesforce-incident#Status]], plus the proposed custom fields [[salesforce-incident#Network_Event_Id__c]] and [[salesforce-incident#Customer_Visible__c]], and on the Asset side [[salesforce-asset#Network_Service_Identifier__c]]. Which Assets an Incident affects is recorded through the proposed junction described in [[salesforce-incident]]. See that note for full field definitions and standard-vs-proposed status; this document does not repeat it.

## Event handling
Correlation to an existing Incident uses [[salesforce-incident#Network_Event_Id__c]], not the Incident's own record id, so a replayed NMS event updates rather than duplicates. An Incident with zero linked Assets is never customer-visible regardless of its flag — visibility is computed from having at least one linked Asset, not asserted independently.

## Security and observability
The portal never queries the NMS or any technical alarm detail directly; it only reads Incident and the Incident–Asset link already resolved in Salesforce. The banner shows only a customer-safe summary (category, window, status), never the raw event payload.

## Open decisions
Whether the target org's NMS integration is genuinely TMF642-shaped or proprietary; whether a dedicated junction object or a different standard relationship links Incident to Asset; how long a resolved Incident stays visible after closing (if at all); how the home page component's refresh interval balances freshness against load; whether [[salesforce-incident#Customer_Visible__c]] is a field an ops user sets manually or a computed value.
