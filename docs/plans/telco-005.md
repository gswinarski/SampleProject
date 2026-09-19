---
id: PLAN-TELCO-005
title: TELCO-005 analysis plan
type: plan
topic_id: TELCO-005
status: draft
relates_to: []
---

# TELCO-005 analysis plan

## Goal
Document the Experience Cloud pre-sales flow where a customer's postal code resolves to a specific address, that address resolves to an aggregated Premise coverage result, and an out-of-coverage address becomes a Lead.

## Steps and deliverables
1. Confirm scope: coverage decision only, not offer selection, quoting or ordering.
2. Review the BPMN gateways for candidate matching, coverage status and the live-qualification hand-off.
3. Document the proposed Premise object and the Lead fields it drives in the shared data model notes, HLD-style.
4. Verify acceptance criteria and UAT scenarios, including the stale/unknown coverage path.
5. Confirm who the postal-code-to-address provider actually is, and whether Premise's external address id can be reconciled with the TMF673 geographicAddressId already used by address-and-service-qualification.
6. Validate documentation in the app and complete the analysis when ready for a local PR.

## Completion criteria
No broken `doc:` or `[[...]]` references, a readable diagram, explicit assumptions and test coverage for acceptance criteria. The analysis owner confirms readiness. Publication and merge remain separate user actions.
