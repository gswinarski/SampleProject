---
id: SEQ-NMS
title: NMS alarm/event ingestion — sequence
type: sequence
topic_id: OUTAGE
status: draft
relates_to:
- INT-NMS
---

# NMS alarm/event ingestion — sequence

The diagram describes the proposed contract and system responsibilities.

```mermaid
sequenceDiagram
    participant NMS as NMS
    participant ADP as Alarm ingestion adapter
    participant SF as Salesforce (Asset / Incident)
    participant PORTAL as Experience Cloud
    NMS->>ADP: Event (networkEventId, affected identifiers, window/severity)
    ADP-->>NMS: Acknowledge receipt
    ADP->>SF: Resolve Assets by network identifier
    alt Known identifiers
      SF->>SF: Create or update Incident by networkEventId
      SF->>SF: Link resolved Assets to Incident
    else Unknown identifier
      SF->>SF: Log for manual mapping
    end
    PORTAL->>SF: Customer opens home page
    SF-->>PORTAL: Open, customer-visible Incidents linked to this customer's Assets
    NMS->>ADP: Cleared event (same networkEventId)
    ADP->>SF: Resolve and close Incident
```

## Interpretation
The NMS never learns which customers are affected; Salesforce performs that correlation privately. The portal never queries the NMS or the adapter directly — it only reads Incident and Asset state already resolved in Salesforce.
