---
id: AC-OUTAGE
title: Planned works and mass outage notification — acceptance criteria
type: acceptance-criteria
topic_id: OUTAGE
status: draft
relates_to:
- BP-OUTAGE
---

# Planned works and mass outage notification — acceptance criteria

| ID | Given / When | Then |
|---|---|---|
| AC-OUTAGE-01 | NMS event names one or more known network service identifiers | Assets are resolved and linked to the Incident. |
| AC-OUTAGE-02 | NMS event names an unknown network service identifier | The identifier is logged for manual mapping; no Asset is guessed. |
| AC-OUTAGE-03 | New unplanned outage event, no existing Incident for it | A new Incident is created with category, impact and detection time. |
| AC-OUTAGE-04 | Same event reported again by NMS (replay) | The existing Incident is updated, not duplicated. |
| AC-OUTAGE-05 | Incident is marked customer-visible and the logged-in customer has a linked Asset | The portal home page shows the banner. |
| AC-OUTAGE-06 | Incident is customer-visible but the logged-in customer has no linked Asset | No banner is shown to that customer. |
| AC-OUTAGE-07 | Incident has no resolved Asset | The Incident is never shown on the portal, regardless of visibility flag. |
| AC-OUTAGE-08 | NMS reports the condition cleared | The Incident is resolved and closed; the banner stops appearing. |
| AC-OUTAGE-09 | Planned work with a future start time | The banner distinguishes an upcoming window from an active outage. |
| AC-OUTAGE-10 | Incident affects a very large number of Assets | The Incident can be marked a major incident without a separate object. |
