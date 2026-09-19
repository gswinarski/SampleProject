---
id: BP-OUTAGE
title: Planned works and mass outage notification — business process
type: business-process
topic_id: OUTAGE
status: draft
relates_to: []
---

# Planned works and mass outage notification — business process

## Purpose and outcome
Customers whose service is affected by planned maintenance or a mass outage see this on the portal home page before they need to contact support. The outcome is an Incident record that groups the affected services and a portal banner that appears only for customers who actually have an affected service.

## Actors and boundaries
The Network Management System (NMS) is the source of truth for network conditions and reports events through an API; it does not know about customers or contracts. Salesforce owns correlating a reported event to affected customer-facing services and to the Incident that represents it, and owns what is safe to show a customer. The NOC/ops team owns the Incident record itself once created.

## Process flow
1. NMS sends an event identifying the affected network service(s) by their network identifier, the event type (planned work or unplanned outage), severity, and a time window (planned start/end) or a detection time (unplanned).
2. Salesforce resolves each affected network identifier to the Asset that carries it.
3. If an open Incident already tracks this event, update it; otherwise create one, setting its category, impact and time window from the event.
4. Link every resolved Asset to the Incident.
5. Decide whether the Incident is customer-visible. An Incident with no resolved Asset, or explicitly marked internal, is tracked but never shown to a customer.
6. When the NMS later reports the condition cleared, resolve and close the Incident. A closed Incident stops appearing on the portal.

## Rules
An Incident is created from network conditions, not from a customer Case — the reverse direction, a Case referencing an existing Incident, is the only link this process makes toward customer issues (see [Customer issues and faults](doc:BP-ISSUE)). The portal never shows raw network diagnostic detail, only a customer-safe summary, the affected window and the current status. A repeated or replayed NMS event never creates a second Incident for the same condition.

## References
[Data model](doc:DATA-INCIDENT) · [Solution design](doc:SD-OUTAGE)
