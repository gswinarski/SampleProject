---
id: SEQ-ADDRESS
title: Address validation — sequence
type: sequence
topic_id: ADDRESS
status: draft
relates_to:
- INT-ADDRESS
---

# Address validation — sequence

The diagram describes the proposed contract and system responsibilities.

```mermaid
sequenceDiagram
    actor U as Customer or agent
    participant OS as OmniScript
    participant IP as Integration Procedure
    participant REG as TMF673 address registry
    U->>OS: Enter installation address
    OS->>IP: Address data and correlationId
    IP->>REG: Validate or find address
    alt Multiple matches
      REG-->>OS: Candidate list via adapter
      OS-->>U: Select address and unit
      U->>OS: Confirm candidate
    else One match
      REG-->>OS: Address for confirmation via adapter
      U->>OS: Confirm address
    else No match
      REG-->>OS: No candidates
      OS-->>U: Correct input or request manual verification
    else Timeout
      IP-->>OS: Technical error
      OS-->>U: Retry the check
    end
    OS->>OS: Store confirmed address ID if obtained
```

## Interpretation
Error paths remain visible to the agent. Durable business state does not depend on a single HTTP call succeeding.
