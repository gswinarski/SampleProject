---
id: PROJECT-ARCH
title: Communications Cloud architecture
type: architecture
topic_id: PROJECT
status: draft
relates_to: []
---

# Communications Cloud architecture

## System boundaries
The customer portal uses Experience Cloud with the standard Create Case Form component. Salesforce is the sole system of record for this topic: the customer relationship, the Case and its category. Case registration makes no live external integration call — everything it needs to decide (identification, duplicates, classification) is already in Salesforce.

| System | Source of truth |
|---|---|
| Salesforce | Interaction, Case, owner and category |

## Configuration to confirm
Communications Cloud and portal licenses, B2C and asset models, sharing rules, and the Create Case Form component's Signed-In vs. Guest Case Action layouts, whether Web-to-Case is enabled, and the reCAPTCHA version (Experience Builder ships v1 only; v2/v3 needs a custom component) — see [Case registration](doc:TOPIC-CASEREG). The POC does not prescribe unverified industry-package object names.

## Consistency and audit
A confirmed duplicate is linked, never re-registered as a second Case. BPMN doc:ID links open documents in the same analysis context or the exact before/after PR revision.
