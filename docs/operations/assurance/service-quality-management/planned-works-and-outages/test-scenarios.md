---
id: TEST-OUTAGE
title: Planned works and mass outage notification — UAT scenarios
type: test-scenarios
topic_id: OUTAGE
status: draft
relates_to:
- AC-OUTAGE
- SD-OUTAGE
---

# Planned works and mass outage notification — UAT scenarios

| Scenario | Data / action | Expected outcome | Coverage |
|---|---|---|---|
| UAT-O01 | NMS event names two known network identifiers | Both Assets linked to one Incident | AC-OUTAGE-01 |
| UAT-O02 | NMS event names an identifier with no matching Asset | Logged for manual mapping; no Asset guessed | AC-OUTAGE-02 |
| UAT-O03 | First report of a new outage | New Incident created with category and detection time | AC-OUTAGE-03 |
| UAT-O04 | NMS resends the same event | Existing Incident updated, not duplicated | AC-OUTAGE-04 |
| UAT-O05 | Customer with an affected Asset opens the portal home page | Banner is shown | AC-OUTAGE-05 |
| UAT-O06 | Customer without an affected Asset opens the portal home page | No banner shown | AC-OUTAGE-06 |
| UAT-O07 | Incident with no linked Asset | Not shown on any customer's portal | AC-OUTAGE-07 |
| UAT-O08 | NMS reports the outage cleared | Incident closed; banner disappears | AC-OUTAGE-08 |
| UAT-O09 | Planned maintenance scheduled for next week | Banner shows it as upcoming, not active | AC-OUTAGE-09 |
| UAT-O10 | Outage affects a large customer base | Incident can be flagged as major | AC-OUTAGE-10 |

These scenarios have not been executed in Salesforce. Test data must be synthetic.
