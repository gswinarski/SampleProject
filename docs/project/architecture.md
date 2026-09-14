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
The customer portal and Communications Service Console use OmniScript forms. Salesforce manages the customer relationship and Case state. Integration Procedures transform data and call adapters. Durable queues and deduplication belong to the agreed integration layer.

| System | Source of truth |
|---|---|
| Salesforce | Interaction, Case, owner, service decision and external references |
| OSS | Network incidents, Trouble Tickets and technical qualification |
| Address registry | Normalized addresses and identifiers |
| Billing | Invoices, charges and completed adjustments |

## Configuration to confirm
Communications Cloud and portal licenses, OmniStudio runtime, B2C and asset models, sharing rules, specialist roles and adapters. The POC does not prescribe unverified industry-package object names.

## Consistency and audit
Case and integration states are separate. Retries and repeated events do not create duplicates. BPMN doc:ID links open documents in the same analysis context or the exact before/after PR revision.
