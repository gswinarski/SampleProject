---
id: TEST-COVERAGE
title: Postal-code address lookup and coverage check — UAT scenarios
type: test-scenarios
topic_id: COVERAGE
status: draft
relates_to:
- AC-COVERAGE
- SD-COVERAGE
---

# Postal-code address lookup and coverage check — UAT scenarios

| Scenario | Data / action | Expected outcome | Coverage |
|---|---|---|---|
| UAT-C01 | Postal code with three candidate addresses | List shown, none pre-selected | AC-COVERAGE-01 |
| UAT-C02 | Postal code with no matches | Correction requested; no address fabricated | AC-COVERAGE-02 |
| UAT-C03 | Customer picks the second of three candidates | Premise resolved for exactly that candidate | AC-COVERAGE-03 |
| UAT-C04 | Selected Premise has an available coverage result | Coverage confirmed; flow can continue | AC-COVERAGE-04 |
| UAT-C05 | Selected Premise has an unavailable coverage result | Lead created with address and contact | AC-COVERAGE-05 |
| UAT-C06 | Same customer re-checks the same unavailable address | No second Lead created | AC-COVERAGE-06 |
| UAT-C07 | Selected Premise has no coverage result yet | Hand-off to live technical qualification | AC-COVERAGE-07 |
| UAT-C08 | Lookup provider does not respond in time | Technical error shown; no false unavailability | AC-COVERAGE-08 |
| UAT-C09 | Customer picks a different address after seeing a result | Previous result discarded; new address checked | AC-COVERAGE-09 |

Example postal codes and addresses are synthetic. These are proposed UAT scenarios; no operator services are called.
