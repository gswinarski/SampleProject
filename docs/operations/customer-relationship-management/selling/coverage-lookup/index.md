---
id: TOPIC-COVERAGE
title: Postal-code address lookup and coverage check
type: topic
topic_id: COVERAGE
status: draft
relates_to:
- BP-COVERAGE
- AC-COVERAGE
- SD-COVERAGE
- TEST-COVERAGE
---

# Postal-code address lookup and coverage check

> Fictional B2C fiber broadband operator. Status: proposal for review.

- [Business process](doc:BP-COVERAGE)
- [Acceptance criteria](doc:AC-COVERAGE)
- [Solution design](doc:SD-COVERAGE)
- [UAT scenarios](doc:TEST-COVERAGE)

## Diagrams
- [coverage-lookup.bpmn](diagrams/coverage-lookup.bpmn)

## Relationship to other topics
This is the pre-sales, Experience Cloud self-service entry point: a prospective or existing customer checks whether their address is serviceable before an order can start. It reads a pre-aggregated coverage result from [[salesforce-premise]] rather than calling a technical qualification system live on every check. When that aggregated result is unknown or stale, this process hands off to the live, on-demand check already described in [Address validation and FTTH qualification](doc:BP-ADDRESS) (TMF673/TMF645) — the two topics use different freshness strategies for what is conceptually the same question, and [[salesforce-premise]] is the natural place a future analysis could describe how the aggregate gets refreshed.

## Sources and limitations
- [eTOM — process classification](https://www.tmforum.org/open-digital-architecture/process-framework-etom/)
- [TMF673 Geographic Address](https://github.com/tmforum-apis/TMF673_GeographicAddress)
- [Communications Service Console](https://help.salesforce.com/s/articleView?id=ind.Comms_Communications_Cloud_B2C_Agent_Console_Overview.htm&language=en_US&type=5)
- [OmniScript and Integration Procedures](https://help.salesforce.com/s/articleView?id=sf.os_integration_procedure_action_12506.htm&language=en_US&type=5)

Conceptual design for a fictional FTTH operator. Topic names and solutions are project proposals, not eTOM certification or a description of a deployed environment. The postal-code-to-address provider is unspecified today; field names and thresholds require agreement with the operator.
