---
id: INT-POSTALLOOKUP
title: Postal code to address candidates — contract
type: integration
topic_id: COVERAGE
status: draft
relates_to:
- SD-COVERAGE
---

# Postal code to address candidates — contract

## Contract status
Integration proposal for agreement. The provider is unspecified today — this is the application's logical model for whichever provider is selected, not a copied wire-format schema. Verify the actual API version, required fields and enumerations before implementation.

## Reference
[TMF673 Geographic Address](https://github.com/tmforum-apis/TMF673_GeographicAddress) — the closest architectural reference for an address-candidate lookup, even though this specific postal-code-in/candidates-out shape is lighter than a full TMF673 normalization call.

## Request and correlation
postalCode and a requestCorrelationId. No customer identity is sent.

## Response
A list of candidates, each with an externalAddressId (the identifier [[salesforce-premise#External_Address_Id__c]] is keyed on) and a displayLabel carrying enough of the address for the customer to tell candidates apart on the UI. An empty list and a timeout are distinct outcomes.

## Errors, retries and controls
Data validation returns a business error without blind retries. Timeouts and transient failures use bounded retries with backoff. Exceeding the retry limit routes work to a manual handling queue. Requests carry correlationId and a stable deduplication key under the agreed adapter contract. A business data change creates a new operation.

Use managed credentials for server-to-server authorization. Logs contain identifiers and statuses, not secrets. Event processing remembers eventId; older responses do not roll back state.

[Sequence diagram](doc:SEQ-POSTALLOOKUP)
