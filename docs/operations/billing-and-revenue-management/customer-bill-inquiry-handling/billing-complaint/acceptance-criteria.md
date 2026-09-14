---
id: AC-BILL
title: Billing complaints — acceptance criteria
type: acceptance-criteria
topic_id: BILL
status: draft
relates_to:
- BP-BILL
---

# Billing complaints — acceptance criteria

| ID | Given / When | Then |
|---|---|---|
| AC-BILL-01 | Invoice belongs to another customer | Deny access and prevent submission. |
| AC-BILL-02 | Invoice line or evidence is missing | Request the missing information. |
| AC-BILL-03 | An authorized specialist approves the complaint | Record the decision, approver, amount and reason. |
| AC-BILL-04 | Billing confirms the adjustment | Record adjustmentId and send the justified customer response. |
| AC-BILL-05 | An adjustment request is retried | Do not create a second adjustment for the same businessRequestId. |
| AC-BILL-06 | The complaint is rejected | Record and communicate the reason without an adjustment request. |
| AC-BILL-07 | Deadline is exceeded or customer appeals | Escalate under policy and preserve the full decision history. |
