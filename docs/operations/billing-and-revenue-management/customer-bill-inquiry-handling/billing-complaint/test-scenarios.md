---
id: TEST-BILL
title: Billing complaints — UAT scenarios
type: test-scenarios
topic_id: BILL
status: draft
relates_to:
- AC-BILL
- SD-BILL
---

# Billing complaints — UAT scenarios

| Test | Action | Expected outcome | Coverage |
|---|---|---|---|
| UAT-B01 | Select another customer’s invoice | Access denied | AC-BILL-01 |
| UAT-B02 | Submit without an invoice line | Request missing data | AC-BILL-02 |
| UAT-B03 | Approved adjustment and successful billing response | One request, adjustment reference and customer reply | AC-BILL-03, AC-BILL-04 |
| UAT-B04 | Repeat the request after a timeout | No second adjustment | AC-BILL-05 |
| UAT-B05 | Reject the complaint | Reason recorded; no adjustment requested | AC-BILL-06 |
| UAT-B06 | Exceed the deadline, then receive an appeal | Escalation and preserved history | AC-BILL-07 |
