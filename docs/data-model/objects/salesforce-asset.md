---
id: DATA-ASSET
title: Asset — data model
type: data-object
topic_id: PROJECT
status: draft
relates_to:
- BP-OUTAGE
- SD-OUTAGE
---

# Asset — data model

Fields the [Planned works and mass outage notification](doc:TOPIC-OUTAGE) process reads. Every service in the system is represented as an Asset. See [[../README|data model conventions]].

## Standard fields

### Id
Standard. Target of [[salesforce-incident]]'s proposed `Incident_Affected_Asset__c` junction.

### Name
Standard. Displayed to the customer when identifying which of their services an Incident affects.

### AccountId
Standard, lookup to Account. Used to resolve which customer's portal should show a banner for an Incident linked to this Asset.

### ContactId
Standard, lookup to Contact. Alternative/additional identification path for the logged-in Experience Cloud user, alongside [[salesforce-account]].

### Status
Standard, picklist. An inactive or decommissioned Asset should not surface outage banners; confirm the exact status values that exclude an Asset from correlation.

## Proposed (custom) fields

### Network_Service_Identifier__c
Proposed, text (external id, unique). The unique network-side identifier for this service, matching the identifier the NMS reports in its event. This is the field [Planned works and mass outage notification](doc:TOPIC-OUTAGE) uses to resolve an NMS event to the Asset(s) it affects — see [[salesforce-incident]] and [Solution design](doc:SD-OUTAGE).
