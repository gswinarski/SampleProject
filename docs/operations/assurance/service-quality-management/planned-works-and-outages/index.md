---
id: TOPIC-OUTAGE
title: Planned works and mass outage notification
type: topic
topic_id: OUTAGE
status: draft
relates_to:
- BP-OUTAGE
- AC-OUTAGE
- SD-OUTAGE
- TEST-OUTAGE
---

# Planned works and mass outage notification

> Fictional B2C fiber broadband operator. Status: proposal for review.

- [Business process](doc:BP-OUTAGE)
- [Acceptance criteria](doc:AC-OUTAGE)
- [Solution design](doc:SD-OUTAGE)
- [UAT scenarios](doc:TEST-OUTAGE)

## Diagrams
- [mass-outage-notification.bpmn](diagrams/mass-outage-notification.bpmn)

## Scope
This topic is proactive and network-driven: the NMS reports a condition before any customer contacts support. A customer Case may separately reference an open Incident from this topic, but this topic owns creating and closing the Incident itself; how a Case does that referencing is a separate concern, out of scope here.

## Sources and limitations
- [eTOM — process classification](https://www.tmforum.org/open-digital-architecture/process-framework-etom/)
- [TMF642 Alarm Management](https://github.com/tmforum-apis/TMF642_AlarmManagement)
- [Customer Service Incident Management objects and fields](https://help.salesforce.com/s/articleView?id=service.incident_mgmt_objects.htm&language=en_US&type=5)

Conceptual design for a fictional FTTH operator. Topic names and solutions are project proposals, not eTOM certification or a description of a deployed environment. Field names and thresholds require agreement with the operator.
