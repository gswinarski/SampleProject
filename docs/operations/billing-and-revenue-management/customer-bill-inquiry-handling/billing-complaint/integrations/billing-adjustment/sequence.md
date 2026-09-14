---
id: SEQ-BILL
title: Billing adjustment request — sequence
type: sequence
topic_id: BILL
status: draft
relates_to:
- INT-BILL
---

# Billing adjustment request — sequence

The diagram describes the proposed contract and system responsibilities.

```mermaid
sequenceDiagram
    participant Agent as Billing specialist
    participant SF as Salesforce Case
    participant MW as Billing adapter
    participant B as Billing system
    Agent->>SF: Approved complaint decision
    alt Complaint upheld
      SF->>MW: Adjustment with businessRequestId
      MW->>B: Request adjustment
      alt Confirmation
        B-->>MW: adjustmentId and confirmed
        MW-->>SF: Store adjustment reference
        SF-->>Agent: Ready for customer response
      else Timeout or error
        MW->>MW: Deduplicated retry or manual handling
        MW-->>SF: Adjustment not confirmed
      end
    else Rejected
      SF->>SF: Record reason without adjustment
    end
```

## Interpretation
Error paths remain visible to the agent. Durable business state does not depend on a single HTTP call succeeding.
