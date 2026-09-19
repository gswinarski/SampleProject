---
id: PROJECT-TMF
title: TM Forum mapping
type: mapping
topic_id: PROJECT
status: draft
relates_to: []
---

# TM Forum mapping

## Organization principle
Folders reflect selected eTOM operational areas, with local project topics beneath them. This is an orientation map, not a complete representation of a specific GB921 release. Process numbers are not assigned without verification against the licensed framework version.

| Project topic | Reference area | Comment |
|---|---|---|
| Case registration via Experience Cloud | Customer Relationship Management / Customer Interface Management | Shared front door: customer issues and billing complaints both assume a Case already exists when their own process starts. |
| Customer issues and faults | Assurance / Customer Problem Management | Intake also touches customer interaction handling. |
| Billing complaints | Billing & Revenue Management / Customer Bill Inquiry Handling | billing-complaint is a local topic; quality complaints remain under customer problems. |
| Address and FTTH qualification | Fulfillment / preparation for service delivery | address-and-service-qualification is a local topic, not an official eTOM process name. Address validation is a shared capability. |
| Planned works and mass outage notification | Assurance / Service Quality Management | Network-driven, proactive; complements rather than replaces the customer-driven Case flow. |

| Integration | Reference | Boundary |
|---|---|---|
| Technical OSS ticket | TMF621 | Not a billing adjustment. |
| Address registry and validation | TMF673 | A valid address does not establish availability. |
| Technical qualification | TMF645 | Not commercial offer qualification or reservation. |
| Billing adjustment | Operator contract | No standard TMF API is claimed. |
| NMS alarm/event ingestion | TMF642 | Not a customer Trouble Ticket; correlation to customers happens only inside Salesforce. |

## Sources and limitations
- [eTOM — process classification](https://www.tmforum.org/open-digital-architecture/process-framework-etom/)
- [Communications Service Console](https://help.salesforce.com/s/articleView?id=ind.Comms_Communications_Cloud_B2C_Agent_Console_Overview.htm&language=en_US&type=5)
- [OmniScript and Integration Procedures](https://help.salesforce.com/s/articleView?id=sf.os_integration_procedure_action_12506.htm&language=en_US&type=5)

Conceptual design for a fictional FTTH operator. Topic names and solutions are project proposals, not eTOM certification or a description of a deployed environment. Service deadlines and contract versions require agreement with the operator.
