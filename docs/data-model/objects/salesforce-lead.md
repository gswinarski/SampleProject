---
id: DATA-LEAD
title: Lead — data model
type: data-object
topic_id: PROJECT
status: draft
relates_to:
- BP-COVERAGE
- SD-COVERAGE
---

# Lead — data model

Fields [Postal-code address lookup and coverage check](doc:TOPIC-COVERAGE) writes when a checked address is out of coverage. See [[../README|data model conventions]]. Standard fields are the well-known Lead schema; proposed fields are design suggestions, not deployed configuration.

## Standard fields

### LastName
Standard. Required on Lead; captured from the customer at the point coverage is found unavailable.

### Company
Standard. Required on Lead; for a residential FTTH prospect this is commonly set to the customer's own name — confirm the operator's convention.

### Email
Standard. Used together with the requested address to detect a repeat check for the same prospect, per [Solution design](doc:SD-COVERAGE).

### Phone
Standard. Optional alternative contact channel.

### Street
Standard. Set from the resolved candidate's display address, not typed again by the customer.

### City
Standard. Same source as [[salesforce-lead#Street]].

### PostalCode
Standard. The postal code the customer originally entered.

### Country
Standard. Set from the resolved candidate.

### LeadSource
Standard, picklist. Set to a value identifying this process (self-service coverage check) as the origin.

### Status
Standard, picklist. Initial status for a coverage-driven Lead; administrators set the values and downstream ownership.

### Description
Standard, long text. Notes the coverage result and timestamp that produced this Lead, for whoever follows up.

## Proposed (custom) fields

### Requested_Premise__c
Proposed, lookup to [[salesforce-premise]]. Links this Lead back to the specific out-of-coverage address, so a later coverage refresh on that Premise can identify prospects to notify. Open decision in [Solution design](doc:SD-COVERAGE): this is the field that would drive any future "notify when available" capability, which is out of scope for this analysis.
