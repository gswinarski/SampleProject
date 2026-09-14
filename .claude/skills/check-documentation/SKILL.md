---
name: check-documentation
description: Check documentation consistency before publication.
---

# check-documentation

Call validate. Report invalid IDs, references and BPMN structure. Test warnings require human assessment; valid syntax does not prove business correctness.

Check doc:ID links in bpmn:documentation and Markdown references to step IDs. Linked documents must exist in the same analysis or exact review version. New topic documents require a readable title. Structural validation does not replace business review of gateways and scenarios.
