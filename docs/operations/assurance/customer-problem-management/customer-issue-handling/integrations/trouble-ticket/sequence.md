---
id: SEQ-TICKET
title: Submit an issue to OSS — sequence
type: sequence
topic_id: ISSUE
status: draft
relates_to:
- INT-TICKET
---

# Submit an issue to OSS — sequence

The diagram describes the proposed contract and system responsibilities.

```mermaid
sequenceDiagram
    actor K as Customer
    participant SF as Salesforce Case
    participant IP as Integration Procedure
    participant MW as Adapter and queue
    participant OSS as OSS Trouble Ticket
    K->>SF: Report an issue
    SF->>SF: Save Case and integrationState=pending
    SF->>IP: Submit complete report
    IP->>MW: Request with correlationId
    MW->>OSS: Create or find ticket
    alt OSS responds
      OSS-->>MW: externalTicketId and status
      MW-->>SF: Link ticket to Case
    else Timeout
      MW->>MW: Retry with the same key
      MW-->>SF: Integration pending
    end
    OSS-->>MW: Status change event
    MW->>MW: Deduplicate eventId
    MW-->>SF: Update technical status
    SF-->>K: Progress notification
```

## Interpretation
Error paths remain visible to the agent. Durable business state does not depend on a single HTTP call succeeding.
