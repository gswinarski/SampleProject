---
id: TEST-ISSUE
title: FTTH customer issues and faults — UAT scenarios
type: test-scenarios
topic_id: ISSUE
status: draft
relates_to:
- AC-ISSUE
- SD-ISSUE
---

# FTTH customer issues and faults — UAT scenarios

| Scenario | Data / action | Expected outcome | Coverage |
|---|---|---|---|
| UAT-I01 | Portal: a customer with one FTTH service reports no internet | One Case with a reference and portal channel | AC-ISSUE-01 |
| UAT-I02 | Agent cannot verify the caller | No data disclosure; controlled verification | AC-ISSUE-02 |
| UAT-I03 | Form lacks symptoms or matches two possible services | More information required; no OSS call | AC-ISSUE-03 |
| UAT-I04 | Same customer reports the same fault again | Contact linked to the existing case | AC-ISSUE-04 |
| UAT-I05 | OSS reports a widespread outage covering the address | One shared incident; individual Case communication retained | AC-ISSUE-05 |
| UAT-I06 | Ticket creation times out, then retries | Case preserved; one ticket in OSS | AC-ISSUE-06 |
| UAT-I07 | Same eventId arrives twice, followed by an older status | No duplicate notification or status rollback | AC-ISSUE-07 |
| UAT-I08 | Clock exceeds the configured threshold | Escalation with reason and history | AC-ISSUE-08 |
| UAT-I09 | OSS resolves the ticket; customer confirms service works | Customer reply and correct Case closure | AC-ISSUE-09 |
| UAT-I10 | Customer reports recurrence during the reopening period | Continuous history and renewed diagnostics | AC-ISSUE-10 |
| UAT-I11 | Customer disputes an invoice charge | Routing to the billing complaint process | AC-ISSUE-11 |

These scenarios have not been executed in Salesforce. Test data must be synthetic.
