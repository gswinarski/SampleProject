---
id: BP-COVERAGE
title: Postal-code address lookup and coverage check — business process
type: business-process
topic_id: COVERAGE
status: draft
relates_to: []
---

# Postal-code address lookup and coverage check — business process

## Purpose and outcome
A customer starting an order on the Experience Cloud portal learns quickly whether their address can be served, without typing a full address by hand. The outcome is either confirmation that the address is in coverage, ready for offer selection, or a registered Lead for an address that is not.

## Actors and boundaries
The customer supplies a postal code and then picks their exact address from a list; an external, currently unspecified provider resolves a postal code to candidate addresses. Salesforce owns matching a selected address to its aggregated coverage record and deciding what happens next. This process ends at the coverage decision — offer selection and ordering are out of scope, and so is how the aggregated coverage data itself gets refreshed.

## Process flow
1. The customer enters a postal code on the order-capture page.
2. Salesforce requests address candidates for that postal code from the external lookup provider. Each candidate carries a unique identifier and the display text the customer needs to tell addresses apart.
3. If no candidates are returned, let the customer correct the postal code; never proceed without a specific address.
4. The customer selects one candidate. Never proceed with the first or only-seeming candidate automatically — the selection is always explicit.
5. Resolve the selected candidate's identifier to a [[salesforce-premise]] record. Create one if this is the first time this address has been looked up.
6. Read the Premise's aggregated coverage status.
7. If available, confirm coverage to the customer and let the flow continue to offer selection.
8. If unavailable, register a Lead capturing the customer's contact details and the requested address, and tell the customer they are outside the current coverage area.
9. If the aggregated result is unknown or older than the agreed freshness threshold, hand off to the live technical qualification described in [Address validation and FTTH qualification](doc:BP-ADDRESS) rather than guessing.

## Rules
A postal code alone is never sufficient to decide coverage — only a specific selected address is. A stale aggregated result is surfaced as stale, never silently treated as available. Every out-of-coverage address becomes exactly one Lead; a repeat check for the same address and contact does not create a second one.

## References
[Data model](doc:DATA-PREMISE) · [Solution design](doc:SD-COVERAGE)
