---
id: BP-ADDRESS
title: Address validation and FTTH qualification — business process
type: business-process
topic_id: ADDRESS
status: draft
relates_to: []
---

# Address validation and FTTH qualification — business process

## Purpose and outcome
An agent or customer obtains a verified installation address and an independent technical FTTH availability result. A valid address does not confirm availability or reserve resources.

## Process flow
1. The portal customer or agent enters country, city, street, building number and optional unit. Retain the original input for comparison.
2. The address registry normalizes the input and finds candidates. No matches leads to correction or manual verification.
3. If several addresses match, the user selects the specific candidate. Never automatically choose the first suggestion.
4. Request a unit number if required to qualify a multi-unit building unambiguously. Then confirm the address and its external identifier.
5. Request technical qualification for the address and FTTH service type. Outcomes include available, unavailable or pending/unknown, with a reason and timestamp.
6. If further checks are needed, save the qualification identifier and await an update. An API timeout is a technical error, not evidence of no coverage.
7. Show the result and its freshness. Changing the address or unit invalidates the previous result for this form and requires another check.

## Boundaries
Offer selection, contracts, ordering and promises of a specific installation date are outside scope. TMF673 concerns addresses; TMF645 concerns service qualification. Commercial offer qualification is not part of this topic.

## Responsibilities
Salesforce manages the interaction and stores the result. The registry owns address identity. The OSS qualification system owns technical availability. The agent decides whether an ambiguous case needs escalation.
