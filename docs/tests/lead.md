---
id: TEST-001
type: tests
status: draft
relates_to: ['REQ-001', 'PROC-001', 'lead_1']
---

> Fictional example — demonstration material.

# UAT scenarios

## Successful conversion
Given a lead with complete details
When the sales representative converts the lead
Then an associated Account and Contact exist.

## Missing information
Conversion is blocked when required information is missing.

## Missing qualification
Given a lead without confirmed qualification
When the sales representative attempts conversion
Then conversion is blocked.

## Confirmed qualification
Given complete details and confirmed qualification
When conversion takes place
Then the Account and Contact are linked.
