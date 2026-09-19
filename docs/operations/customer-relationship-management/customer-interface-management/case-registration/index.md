---
id: TOPIC-CASEREG
title: Case registration via Experience Cloud
type: topic
topic_id: CASEREG
status: draft
relates_to:
- BP-CASEREG
- AC-CASEREG
- SD-CASEREG
- TEST-CASEREG
---

# Case registration via Experience Cloud

> Fictional B2C fiber broadband operator. Status: proposal for review.

- [Business process](doc:BP-CASEREG)
- [Acceptance criteria](doc:AC-CASEREG)
- [Solution design](doc:SD-CASEREG)
- [UAT scenarios](doc:TEST-CASEREG)

## Diagrams
- [case-registration.bpmn](diagrams/case-registration.bpmn)

## Relationship to other topics
This topic owns the generic "front door" through which every customer contact becomes a Case: identification, the self-service form, duplicate detection and classification. It does not repeat the technical fault/quality investigation already described in [Customer issues and faults](doc:TOPIC-ISSUE), nor the financial review in [Billing complaints](doc:TOPIC-BILL) — once a Case is classified, this process hands off into those topics. Treat this topic's business process and data model as a shared dependency of both.

## Sources and limitations
- [eTOM — process classification](https://www.tmforum.org/open-digital-architecture/process-framework-etom/)
- [TMF621 Trouble Ticket](https://www.tmforum.org/resources/standard/tmf621-trouble-ticket-management-api-rest-specification-r19-0-0/)
- [Create Case Form component](https://help.salesforce.com/s/articleView?id=experience.rss_case_creation.htm&language=en_US&type=5)
- [Set Up Web-to-Case for Guest Users](https://help.salesforce.com/s/articleView?id=platform.rss_guest_users.htm&language=en_US&type=5)
- [Case object reference](https://developer.salesforce.com/docs/atlas.en-us.object_reference.meta/object_reference/sforce_api_objects_case.htm)

Conceptual design for a fictional FTTH operator. Topic names and solutions are project proposals, not eTOM certification or a description of a deployed environment. Field names and record types require agreement with the operator.
