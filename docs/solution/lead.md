---
id: SOL-001
type: solution
status: draft
relates_to: ['REQ-001', 'PROC-001']
---

> Fictional example — demonstration material.

# Solution design

Objects: Lead, Account, Contact, Opportunity.

## Proposed implementation
Standard Lead conversion; field mappings require confirmation in the target organization.

## Solution change
Proposed Lead.Qualification_Confirmed__c field and a check on the IsConverted transition. The blocking mechanism requires validation in the target organization.
