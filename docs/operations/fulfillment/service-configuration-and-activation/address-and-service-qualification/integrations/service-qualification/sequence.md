---
id: SEQ-QUALIFICATION
title: FTTH qualification — sequence
type: sequence
topic_id: ADDRESS
status: draft
relates_to:
- INT-QUALIFICATION
---

# FTTH qualification — sequence

The diagram describes the proposed contract and system responsibilities.

```mermaid
sequenceDiagram
    actor U as Customer or agent
    participant SF as Salesforce OmniScript
    participant IP as Qualification adapter
    participant OSS as OSS TMF645
    U->>SF: Confirm address and service type
    SF->>IP: AddressId, unit, FTTH, correlationId
    IP->>OSS: Check technical qualification
    alt Final result
      OSS-->>IP: Availability and reason
      IP-->>SF: qualificationId, result, checkedAt
      SF-->>U: Result with freshness information
    else Pending
      OSS-->>IP: Qualification reference
      IP-->>SF: Pending
      OSS-->>IP: Later result
      IP-->>SF: Result with correlationId
      SF->>SF: Apply only to the current address
    else Timeout
      IP-->>SF: Technical error, not unavailable
      SF-->>U: Retry or refer to an agent
    end
```

## Interpretation
Error paths remain visible to the agent. Durable business state does not depend on a single HTTP call succeeding.
