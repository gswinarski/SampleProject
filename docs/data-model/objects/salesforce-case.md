---
id: DATA-CASE
title: Case — data model
type: data-object
topic_id: PROJECT
status: draft
relates_to:
- BP-CASEREG
- SD-CASEREG
---

# Case — data model

Fields the [Case registration](doc:TOPIC-CASEREG) process reads or writes. See [[../README|data model conventions]] for how fields are documented and linked. Standard fields are verified against the [Case object reference](https://developer.salesforce.com/docs/atlas.en-us.object_reference.meta/object_reference/sforce_api_objects_case.htm); proposed fields are design suggestions, not deployed configuration.

## Standard fields

### CaseNumber
Standard, auto-number. The confirmation number given to the customer at registration (AC-CASEREG-01, AC-CASEREG-10).

### Subject
Standard, text. Short summary captured on the case form; also the text used for Knowledge deflection.

### Description
Standard, long text. Full description captured on the case form; maps loosely to the TMF621 `note` attribute.

### Status
Standard, picklist. Case lifecycle state. Registration always creates a Case in an initial open status; downstream topics own later transitions.

### Origin
Standard, picklist. Broad channel of the contact (for example Web, Phone, Email). Registration sets this to a portal-facing value; see [[salesforce-case#Registration_Channel_Detail__c]] for the finer distinction Experience Cloud needs.

### Priority
Standard, picklist. Business urgency; maps loosely to the TMF621 `priority` attribute. Not set by registration itself — defaulted or set by the specialist topic that takes the Case.

### Type
Standard, picklist. Broad category (for example Question, Problem). Used together with [[salesforce-case#RecordTypeId]] to route the Case at the end of registration.

### Reason
Standard, picklist. Finer reason within a Type; optional at registration, may be refined downstream.

### RecordTypeId
Standard, lookup to RecordType. Distinguishes the registration outcome — for example a general-inquiry Case from one that hands off to [Customer issues and faults](doc:BP-ISSUE) or [Billing complaints](doc:BP-BILL). Record Types and their page layouts are configuration to confirm in the target org.

### AccountId
Standard, lookup to Account. Set for an authenticated customer; see [[salesforce-account]].

### ContactId
Standard, lookup to Contact. Set for an authenticated customer via the Signed-In User Case Action; see [[salesforce-contact]].

### SuppliedName
Standard, text. Guest visitor's given name, captured by the Guest User Case Action when there is no [[salesforce-case#ContactId]].

### SuppliedEmail
Standard, text. Guest visitor's email, captured by the Guest User Case Action.

### SuppliedPhone
Standard, text. Guest visitor's phone, captured by the Guest User Case Action.

### ParentId
Standard, lookup to Case. The standard mechanism for a related/merged Case; one candidate for recording a duplicate match — see the open decision against [[salesforce-case#Duplicate_Of__c]].

### EntitlementId
Standard, lookup to Entitlement. Not set by registration; relevant once a specialist topic applies an SLA.

### ClosedDate
Standard, date/time. Not set by registration; included for completeness since it is part of the same lifecycle.

### OwnerId
Standard, lookup to User or Queue. Registration assigns an initial owner or queue; ownership may change once a specialist topic takes the Case.

## Proposed (custom) fields

### Service_Reference__c
Proposed, lookup or text. Identifies the specific FTTH service the contact concerns, without copying the OSS inventory into Salesforce. Maps to the TMF621 `relatedEntity` attribute. Confirm whether the target org's asset/service model supports a real lookup or requires a text reference.

### Registration_Channel_Detail__c
Proposed, picklist. Distinguishes "Experience Cloud — authenticated" from "Experience Cloud — guest" (and future channels), finer than the standard [[salesforce-case#Origin]] value. Set once, at registration, from which Case Action created the record.

### External_Reference_Id__c
Proposed, text. Correlation/deduplication key carried forward to whichever downstream integration a specialist topic uses (the same role as `correlationId`/`externalTicketId` in the [customer issues and faults solution design](doc:SD-ISSUE)). Populated by registration only when a category with a known downstream integration is selected.

### Duplicate_Of__c
Proposed, lookup to Case. An explicit "possible duplicate" link set by the duplicate-check step, kept separate from a confirmed merge. Open decision: whether this field is worth its own semantics or the standard [[salesforce-case#ParentId]] should be reused instead — see [Solution design](doc:SD-CASEREG).

### Consent_Data_Processing__c
Proposed, checkbox. Captures a guest visitor's data-processing consent at registration, since no authenticated Contact/consent record exists yet at that point. Open decision: whether consent belongs on the Case at all, or on a dedicated consent record reconciled to the Contact once one exists.
