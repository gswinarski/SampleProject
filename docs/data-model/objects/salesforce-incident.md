---
id: DATA-INCIDENT
title: Incident — data model
type: data-object
topic_id: PROJECT
status: draft
relates_to:
- BP-OUTAGE
- SD-OUTAGE
---

# Incident — data model

Fields the [Planned works and mass outage notification](doc:TOPIC-OUTAGE) process reads or writes. See [[../README|data model conventions]]. Standard fields are verified against [Customer Service Incident Management Objects and Fields](https://help.salesforce.com/s/articleView?id=service.incident_mgmt_objects.htm&language=en_US&type=5); proposed fields are design suggestions, not deployed configuration.

## Standard fields

### IncidentNumber
Standard, auto-number. Read-only identifier an ops user or report can reference; not shown to the customer directly (the portal shows the category and window instead).

### Category
Standard, picklist. Used to distinguish planned maintenance from an unplanned outage; administrators set the values.

### SubCategory
Standard, picklist, dependent on Category. Optional finer classification.

### Description
Standard, long text. Internal description of the condition; not the customer-facing banner text.

### DetectedDateTime
Standard, date/time. When an unplanned outage was first detected — set from the NMS event's detection time.

### StartDateTime
Standard, date/time. When the condition began, or the planned start of scheduled work.

### EndDateTime
Standard, date/time. Planned end of scheduled work; for an outage, set only once resolved.

### Impact
Standard, picklist. The effect on customer experience; administrators set the values.

### Priority
Standard, picklist, derived from Impact and Urgency.

### IsMajorIncident
Standard, checkbox ("Major Incident"). Marks an incident as widespread and business-critical, without a separate object.

### ParentIncidentId
Standard, lookup to Incident. Available if multiple reported conditions are grouped under one parent incident.

### ReportedMethod
Standard, picklist. How the incident was reported to customer service; set to a value representing "NMS" for this process.

### Status
Standard, picklist. Administrators set the values (for example open, in progress, closed).

### StatusCode
Standard, dependent status code derived from [[salesforce-incident#Status]].

### ResolutionDateTime
Standard, date/time. Set when the NMS reports the condition cleared.

### ResolvedBy
Standard, lookup to User. Who or what closed the incident; may be a system/integration user for automated resolution.

### OwnerId
Standard, lookup to User or Queue ("Incident Owner"). The NOC team or queue that owns triage.

## Proposed (custom) fields

### Network_Event_Id__c
Proposed, text (external id, unique). The NMS's own event identifier — the deduplication key so a replayed event updates this Incident instead of creating a duplicate. Maps to the TMF642 alarm's own identifier.

### Customer_Visible__c
Proposed, checkbox. Whether this Incident is eligible to appear on the portal home page. Computed together with "has at least one linked Asset" per [Solution design](doc:SD-OUTAGE) — the field alone does not guarantee visibility.

## Related object (proposed)

### Incident_Affected_Asset__c
Proposed junction object linking an Incident to each [[salesforce-asset]] it affects (lookup to Incident, lookup to Asset). Open decision in [Solution design](doc:SD-OUTAGE): whether a dedicated junction is worth its own object, or a different standard relationship covers this in the target org.
