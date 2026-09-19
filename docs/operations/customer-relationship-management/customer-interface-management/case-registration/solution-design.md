---
id: SD-CASEREG
title: Case registration via Experience Cloud — solution design
type: solution-design
topic_id: CASEREG
status: draft
relates_to:
- BP-CASEREG
- AC-CASEREG
---

# Case registration via Experience Cloud — solution design

## Component responsibilities
| Component | Proposed responsibility | Confirm in the target org |
|---|---|---|
| Experience Cloud site | Hosts the self-service case form for authenticated and guest visitors | Site licenses, guest user profile, sharing model |
| Create Case Form component | Renders the form, runs Knowledge deflection, submits through a Global Action | Header/confirmation text, deflection category, file attachments (unavailable to guests) |
| Signed-In User Case Action | Global Action + action layout used for authenticated submissions | Which fields are visible/required on this layout |
| Guest User Case Action | Global Action + action layout used for unauthenticated submissions; requires Web-to-Case enabled | reCAPTCHA availability (Experience Builder ships v1 only; v2/v3 needs a custom Lightning component) |
| Case | The registered customer case: category, status, owner, channel and history | Record Types and permitted status transitions |
| Account / Contact | Customer identification for authenticated visitors | Person Accounts or Account/Contact model |
| Flow / duplicate rule | Duplicate detection against contact, service and category before Case creation | Matching window and fields used for the match |
| Knowledge | Suggests articles from the typed subject/description before submission | Data category mapping used for deflection |

## Data model
Case registration reads and writes the fields documented in [[salesforce-case]], most directly [[salesforce-case#Status]], [[salesforce-case#Origin]], [[salesforce-case#Type]], [[salesforce-case#RecordTypeId]], [[salesforce-case#ContactId]], [[salesforce-case#AccountId]], [[salesforce-case#SuppliedName]], [[salesforce-case#SuppliedEmail]], [[salesforce-case#SuppliedPhone]] and [[salesforce-case#ParentId]], plus the proposed custom fields [[salesforce-case#Service_Reference__c]], [[salesforce-case#Registration_Channel_Detail__c]], [[salesforce-case#External_Reference_Id__c]], [[salesforce-case#Duplicate_Of__c]] and [[salesforce-case#Consent_Data_Processing__c]]. Guest identification additionally depends on [[salesforce-contact]] and [[salesforce-account]] once a guest contact is reconciled to a known customer. See [[salesforce-case]] for full field definitions, standard-vs-proposed status and the TMF621 attribute each proposed field maps from — this document does not repeat that detail.

## Event handling
Duplicate detection runs before Case creation, not after, so a confirmed match never produces a second Case. When no confident match exists, prefer creating a new Case over silently attaching to an uncertain one; classification recorded here is corrected, not overwritten, by downstream specialist teams.

## Security and observability
Guest submissions never expose data belonging to another contact, even on a near-match. Verification-challenge failures and duplicate-match decisions are recorded on the Case for audit. Attachments are only accepted from authenticated visitors.

## Open decisions
Whether [[salesforce-case#Duplicate_Of__c]] is a distinct field or the standard [[salesforce-case#ParentId]] is reused for possible duplicates; which reCAPTCHA version and hosting approach the target org uses; where [[salesforce-case#Consent_Data_Processing__c]] should actually live (Case field vs. a dedicated consent record); the exact duplicate-matching window and field set; Knowledge data category mapping for deflection.
