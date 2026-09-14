---
id: BP-ISSUE
title: FTTH customer issues and faults — business process
type: business-process
topic_id: ISSUE
status: draft
relates_to: []
---

# FTTH customer issues and faults — business process

## Purpose and outcome
The customer receives a unique case number, an owner and information about next steps. The outcome is a resolution communicated to the customer or a transfer of a billing complaint to its dedicated process.

## Actors and boundaries
A B2C customer reports an issue through the portal, or an agent records the contact in Communications Service Console. Customer service owns the Case and communication. OSS owns diagnostics and the technical Trouble Ticket. Billing owns financial decisions.

## Process flow
1. Receive the report and identify the customer and FTTH service. Use the authenticated portal session or the agreed agent verification procedure.
2. Collect the description, installation address, onset time, symptoms and safe attachments. Request missing information; do not guess which service is affected.
3. Check open cases for this customer and service. For a confirmed duplicate, add the contact to the existing case and provide its reference.
4. Distinguish a fault, a service-quality complaint and a billing complaint. A quality complaint remains a customer case and may require linked technical diagnostics.
5. For faults, perform initial diagnostics and check known network incidents. Link the case to an existing incident or create an OSS ticket.
6. Update the customer when the status changes. Escalate after the configured deadline without creating another Trouble Ticket.
7. Communicate the resolution and request confirmation. Handle missing confirmation according to the agreed policy; link recurrence to the existing history.

## Rules
Case and Trouble Ticket have separate lifecycles. Technical resolution in OSS does not automatically close the customer's complaint. Response, escalation and reopening periods are project parameters, not statutory deadlines defined by this example.

## References
[Identification details](doc:STEP-IDENTIFY) · [Classification](doc:STEP-CLASSIFY) · [OSS integration](doc:INT-TICKET)
