---
id: TEST-ADDRESS
title: Address validation and FTTH qualification — UAT scenarios
type: test-scenarios
topic_id: ADDRESS
status: draft
relates_to:
- AC-ADDRESS
- SD-ADDRESS
---

# Address validation and FTTH qualification — UAT scenarios

| Test | Data / action | Outcome | Coverage |
|---|---|---|---|
| UAT-A01 | Abbreviated street name with one match | Normalized address for confirmation | AC-ADDR-01 |
| UAT-A02 | Two towns with the same name | Explicit candidate selection | AC-ADDR-02 |
| UAT-A03 | New building unknown to the registry | Correction or manual verification | AC-ADDR-03 |
| UAT-A04 | Multi-unit building without a unit number | Additional information required | AC-ADDR-04 |
| UAT-A05 | Address with available FTTH | Available result with timestamp and references | AC-ADDR-05 |
| UAT-A06 | Valid address outside coverage | Unavailable result with a reason | AC-ADDR-06 |
| UAT-A07 | OSS returns pending, then a final result | Correlation preserved and state updated | AC-ADDR-07 |
| UAT-A08 | Each integration times out | Technical error; no false unavailability | AC-ADDR-08 |
| UAT-A09 | Change unit after an available result | Another check required | AC-ADDR-09 |
| UAT-A10 | Responses arrive in reverse order | Current address result remains authoritative | AC-ADDR-10 |

Example addresses are synthetic. These are proposed UAT scenarios; no operator services are called.
