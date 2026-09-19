---
id: AC-CASEREG
title: Case registration via Experience Cloud — acceptance criteria
type: acceptance-criteria
topic_id: CASEREG
status: draft
relates_to:
- BP-CASEREG
---

# Case registration via Experience Cloud — acceptance criteria

| ID | Given / When | Then |
|---|---|---|
| AC-CASEREG-01 | Authenticated customer with one FTTH service submits a complete form | One Case with a confirmation number; contact, account and channel detail recorded. |
| AC-CASEREG-02 | Guest visitor has not solved the verification challenge | The form does not submit; no Case is created. |
| AC-CASEREG-03 | Guest visitor submits without a name, email or phone | The gap is shown; no Case is created. |
| AC-CASEREG-04 | Required field from the action layout is missing | Specific gaps are shown; the Case is not created. |
| AC-CASEREG-05 | A matching open Case exists for the same contact and service | The new contact is linked to the existing Case; no second Case is created. |
| AC-CASEREG-06 | Category selected is a technical fault or quality concern | The Case is created and handed to the customer issues and faults process. |
| AC-CASEREG-07 | Category selected is a disputed charge | The Case is created and handed to the billing complaints process. |
| AC-CASEREG-08 | Category selected is a general inquiry | The Case is created and remains queued for direct handling; no hand-off occurs. |
| AC-CASEREG-09 | Web-to-Case is disabled in the target org | The guest path is unavailable; the authenticated path is unaffected. |
| AC-CASEREG-10 | Case is created successfully | Customer receives a confirmation containing the Case number. |
