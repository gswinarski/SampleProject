---
id: AC-COVERAGE
title: Postal-code address lookup and coverage check — acceptance criteria
type: acceptance-criteria
topic_id: COVERAGE
status: draft
relates_to:
- BP-COVERAGE
---

# Postal-code address lookup and coverage check — acceptance criteria

| ID | Given / When | Then |
|---|---|---|
| AC-COVERAGE-01 | Valid postal code with several matching addresses | A list of candidates is shown; none is pre-selected. |
| AC-COVERAGE-02 | Postal code matches no address | The customer can correct it; no candidate is fabricated. |
| AC-COVERAGE-03 | Customer selects a candidate | The Premise for that exact candidate is resolved, never a different one. |
| AC-COVERAGE-04 | Premise coverage status is available | Coverage is confirmed and the flow can continue. |
| AC-COVERAGE-05 | Premise coverage status is unavailable | A Lead is created with the requested address and contact details. |
| AC-COVERAGE-06 | Same contact and address checked again while still unavailable | No second Lead is created. |
| AC-COVERAGE-07 | Premise has no coverage status yet, or it is older than the freshness threshold | The flow hands off to live technical qualification instead of guessing. |
| AC-COVERAGE-08 | Postal-code lookup provider times out | A technical error is shown; the address is not assumed unavailable. |
| AC-COVERAGE-09 | Customer changes the selected address after a coverage result | The previous result no longer applies; the new address is checked again. |
