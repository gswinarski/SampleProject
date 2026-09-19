---
id: SEQ-POSTALLOOKUP
title: Postal code to address candidates — sequence
type: sequence
topic_id: COVERAGE
status: draft
relates_to:
- INT-POSTALLOOKUP
---

# Postal code to address candidates — sequence

The diagram describes the proposed contract and system responsibilities.

```mermaid
sequenceDiagram
    actor K as Customer
    participant SF as Salesforce (order capture)
    participant ADP as Postal-code lookup adapter
    participant EXT as External address provider
    K->>SF: Enter postal code
    SF->>ADP: postalCode + requestCorrelationId
    ADP->>EXT: Lookup
    alt Candidates found
      EXT-->>ADP: List of {externalAddressId, displayLabel}
      ADP-->>SF: Candidates
      SF-->>K: Show list for selection
      K->>SF: Select one candidate
      SF->>SF: Resolve or create Premise by externalAddressId
      SF-->>K: Coverage result (available / unavailable / unknown)
    else No candidates
      EXT-->>ADP: Empty list
      ADP-->>SF: Empty list
      SF-->>K: Ask to correct postal code
    else Timeout
      ADP->>ADP: Retry with the same key
      ADP-->>SF: Technical error if retries exhausted
    end
```

## Interpretation
The external provider never sees which candidate the customer picked, only the postal code query. The coverage decision itself never leaves Salesforce.
