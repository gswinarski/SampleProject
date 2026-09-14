---
id: SD-BILL
title: Billing complaints — solution design
type: solution-design
topic_id: BILL
status: draft
relates_to:
- BP-BILL
- AC-BILL
---

# Billing complaints — solution design

## Components and configuration
Use Case for the customer's billing complaint, an agent Console view and a portal/OmniScript intake form. Record the invoice and line reference, disputed amount, currency, evidence and decision. These are logical design concepts; confirm actual fields and Record Types in the target org.

Flow guides required stages and records the decision. Adjustment approval requires an appropriate role and financial limit under the operator's matrix. An Integration Procedure sends the request to the billing adapter; its durable queue handles retry and deduplication by businessRequestId.

## State
Case: collecting information → investigation → decision → awaiting adjustment (if applicable) → response → closed. Integration state is separate: pending/sent/confirmed/failed. Notify the customer of a completed adjustment only after confirmed.

## Contract
The [adjustment contract](doc:INT-BILL) is a project proposal, not a TMF621 implementation. Agree the exact API and amount model with the billing provider.

## Controls
Validate invoice ownership server-side. Restrict adjustment approval, audit the approver and decision, and avoid logging payment or customer secrets. Confirm licenses, sharing rules, approval thresholds, deadlines and retry limits before implementation.
