---
id: TOPIC-ADDRESS
title: Address validation and FTTH qualification
type: topic
topic_id: ADDRESS
status: draft
relates_to:
- BP-ADDRESS
- AC-ADDRESS
- SD-ADDRESS
- TEST-ADDRESS
---

# Address validation and FTTH qualification

> Fictional B2C fiber broadband operator. Status: proposal for review.

- [Business process](doc:BP-ADDRESS)
- [Acceptance criteria](doc:AC-ADDRESS)
- [Solution design](doc:SD-ADDRESS)
- [UAT scenarios](doc:TEST-ADDRESS)

## Diagrams
- [address-and-availability.bpmn](diagrams/address-and-availability.bpmn)

## Related topics
[Postal-code address lookup and coverage check](doc:TOPIC-COVERAGE) screens addresses earlier, against a cached aggregate, and calls into this process only when that cache is missing or stale — this topic remains the authority for a live, on-demand TMF673/TMF645 result.

## Sources and limitations
- [eTOM — process classification](https://www.tmforum.org/open-digital-architecture/process-framework-etom/)
- [Communications Service Console](https://help.salesforce.com/s/articleView?id=ind.Comms_Communications_Cloud_B2C_Agent_Console_Overview.htm&language=en_US&type=5)
- [OmniScript and Integration Procedures](https://help.salesforce.com/s/articleView?id=sf.os_integration_procedure_action_12506.htm&language=en_US&type=5)

Conceptual design for a fictional FTTH operator. Topic names and solutions are project proposals, not eTOM certification or a description of a deployed environment. Service deadlines and contract versions require agreement with the operator.
