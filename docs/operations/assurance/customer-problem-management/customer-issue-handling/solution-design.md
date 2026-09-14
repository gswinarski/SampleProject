---
id: SD-ISSUE
title: FTTH customer issues and faults — solution design
type: solution-design
topic_id: ISSUE
status: draft
relates_to:
- BP-ISSUE
- AC-ISSUE
---

# FTTH customer issues and faults — solution design

## Component responsibilities
| Component | Proposed responsibility | Confirm in the target org |
|---|---|---|
| Communications Service Console | Customer, service and related Case view | Licenses, application and available components |
| Experience Cloud + OmniScript | Authenticated customer self-service intake | Portal licenses, sharing and OmniScript publication |
| OmniScript | Guided form, symptoms and completeness checks | OmniStudio runtime and available components |
| Case | Customer case, type, channel, status, queue and history | Record Types and permitted status transitions |
| Account/Contact + service reference | Customer–service relationship without copying OSS inventory | Person Accounts or Account/Contact; industry asset model |
| Flow / queues | Routing, ownership and controlled escalation | Priority matrix, calendars and deadline rules |
| Integration Procedures + integration layer | Context assembly and OSS adapter calls | Named Credentials, limits, timeouts and retry strategy |

## Data model and state
Proposed Case information: category, service reference, network incident identifier, externalTicketId, integrationState, correlationId and last update time. These are design concepts, not claims that standard fields with these API names exist.

Separate business status from integration state. Save the Case before submitting work to OSS. A queue/outbox in the integration layer provides retries after failures. Running a Flow alone does not guarantee exactly-once delivery.

## Event handling
Maintain the Case–OSS ticket mapping. Record processed event IDs; older updates must not roll back status. Suppress duplicate customer notifications. Record failures and allow authorized operators to retry manually.

## Security and observability
The portal exposes only the customer's own cases. Do not log secrets or full sensitive payloads. Track correlationId, retry counts and cases without owners. Billing adjustment permissions are separate.

## Open decisions
Communications Cloud/OmniStudio version, subscriber data model, OSS provider, SLA policy, notification channel and attachment retention.
