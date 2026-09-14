---
id: AC-ISSUE
title: FTTH customer issues and faults — acceptance criteria
type: acceptance-criteria
topic_id: ISSUE
status: draft
relates_to:
- BP-ISSUE
---

# FTTH customer issues and faults — acceptance criteria

| ID | Given / When | Then |
|---|---|---|
| AC-ISSUE-01 | Verified customer, selected service and complete submission | One Case and confirmation number; channel and owner recorded. |
| AC-ISSUE-02 | Identity cannot be verified | Service details are not disclosed; the report enters controlled verification. |
| AC-ISSUE-03 | Missing description or service selection | Specific gaps are shown; OSS submission is held. |
| AC-ISSUE-04 | Confirmed duplicate exists | The contact is linked to the existing case; no second ticket is created. |
| AC-ISSUE-05 | Known widespread outage affects the service | The Case references the shared incident and latest available update. |
| AC-ISSUE-06 | OSS is unavailable | The Case remains saved with integration pending; retries use the same key. |
| AC-ISSUE-07 | The same OSS event is received again | Neither the status update nor the customer notification is duplicated. |
| AC-ISSUE-08 | Response deadline is exceeded | The owner receives an escalation with a recorded reason. |
| AC-ISSUE-09 | OSS reports resolution | The customer is notified; closure follows the confirmation policy. |
| AC-ISSUE-10 | Customer reports recurrence within the allowed period | Reopen the case or create a linked case according to policy. |
| AC-ISSUE-11 | Customer disputes a charge | Route to billing rather than treating it as a technical fault. |
