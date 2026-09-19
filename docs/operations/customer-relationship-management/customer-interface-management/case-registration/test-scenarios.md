---
id: TEST-CASEREG
title: Case registration via Experience Cloud — UAT scenarios
type: test-scenarios
topic_id: CASEREG
status: draft
relates_to:
- AC-CASEREG
- SD-CASEREG
---

# Case registration via Experience Cloud — UAT scenarios

| Scenario | Data / action | Expected outcome | Coverage |
|---|---|---|---|
| UAT-CR01 | Authenticated customer with one FTTH service submits a complete form | One Case with a confirmation number and correct contact/account | AC-CASEREG-01 |
| UAT-CR02 | Guest visitor skips the verification challenge | Form does not submit | AC-CASEREG-02 |
| UAT-CR03 | Guest visitor submits without an email or phone | Gap is shown; no Case created | AC-CASEREG-03 |
| UAT-CR04 | Authenticated customer omits a required layout field | Gap is shown; no Case created | AC-CASEREG-04 |
| UAT-CR05 | Same customer submits a second report for the same open fault | Contact linked to the existing Case | AC-CASEREG-05 |
| UAT-CR06 | Customer selects "no internet" as the category | Case created with that category, routed to the owning queue | AC-CASEREG-06 |
| UAT-CR07 | Customer selects "disputed charge" as the category | Case created with that category, routed to the owning queue | AC-CASEREG-07 |
| UAT-CR08 | Customer selects "general question" as the category | Case created and queued for direct handling | AC-CASEREG-08 |
| UAT-CR09 | Web-to-Case is disabled in the test org | Guest path unavailable; authenticated path still works | AC-CASEREG-09 |
| UAT-CR10 | Any successful submission | Customer receives the Case number | AC-CASEREG-10 |

These scenarios have not been executed in Salesforce. Test data must be synthetic.
