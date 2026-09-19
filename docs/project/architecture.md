---
id: PROJECT-ARCH
title: Communications Cloud architecture
type: architecture
topic_id: PROJECT
status: draft
relates_to: []
---

# Communications Cloud architecture

## System boundaries
The customer portal uses Experience Cloud with the standard Create Case Form component. Salesforce is the system of record for the customer relationship, the Case and its category, and for Incident/Asset state. Case registration makes no live external integration call; planned works and mass outage notification is the exception, ingesting events from the NMS.

| System | Source of truth |
|---|---|
| Salesforce | Interaction, Case, owner, category, Incident and Asset |
| NMS | Network alarms/events and their affected network service identifiers |

## Configuration to confirm
Communications Cloud and portal licenses, B2C and asset models, sharing rules, and the Create Case Form component's Signed-In vs. Guest Case Action layouts, whether Web-to-Case is enabled, and the reCAPTCHA version (Experience Builder ships v1 only; v2/v3 needs a custom component) — see [Case registration](doc:TOPIC-CASEREG). Whether Customer Service Incident Management is enabled, and whether the target NMS is genuinely TMF642-shaped — see [Planned works and mass outage notification](doc:TOPIC-OUTAGE). The POC does not prescribe unverified industry-package object names.

## Consistency and audit
A confirmed duplicate Case is linked, never re-registered as a second Case. A replayed NMS event updates its existing Incident rather than creating a duplicate. BPMN doc:ID links open documents in the same analysis context or the exact before/after PR revision.
