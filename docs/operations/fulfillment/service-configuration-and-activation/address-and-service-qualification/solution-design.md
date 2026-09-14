---
id: SD-ADDRESS
title: Address validation and FTTH qualification — solution design
type: solution-design
topic_id: ADDRESS
status: draft
relates_to:
- BP-ADDRESS
- AC-ADDRESS
---

# Address validation and FTTH qualification — solution design

## Components
| Component | Responsibility | Assumption to confirm |
|---|---|---|
| OmniScript in Console and portal | Address entry, candidate selection and result presentation | License and Experience Cloud embedding |
| Integration Procedures | Request aggregation and transformation | OmniStudio runtime and Named Credentials |
| TMF673 adapter | Normalization and external address ID | API version and provider data-quality rules |
| TMF645 adapter | FTTH qualification | Service model and specification identifiers |
| Persistent result storage in Salesforce | Qualification history and response correlation | Industry address model or a controlled extension object |

## Data
Store enteredAddress, validatedAddressId, normalizedAddress, unit, qualificationId, serviceType, result, reason, checkedAt and requestCorrelationId as logical design concepts. Select Salesforce API field names after reviewing the Communications Cloud data model; standard fields with these names are not assumed to exist.

## Integration rules
Qualification requires a confirmed address ID and unit context. The result cache has a configurable validity period and an address+unit+service-type key. Changing any component requires a new request. A response must match the active requestCorrelationId.

## Errors and security
A timeout retains technical-error or pending, never unavailable. Retrying must not duplicate an asynchronous operation. Limit address data in logs; the portal does not directly access technical OSS APIs.

## Open decisions
Registry provider, unit model, qualification validity period, callback/polling mode and mapping from TMF standards to provider contracts.
