---
id: BP-CASEREG
title: Case registration via Experience Cloud — business process
type: business-process
topic_id: CASEREG
status: draft
relates_to: []
---

# Case registration via Experience Cloud — business process

## Purpose and outcome
Every customer contact, whatever its eventual category, becomes exactly one Case with a confirmation number, an owner and a recorded channel. The outcome is either a Case ready for specialist handling (fault, quality, billing) or, for a simple request, a Case handled directly from this process.

## Actors and boundaries
A B2C customer opens the self-service form in Experience Cloud, authenticated or as a guest. Salesforce owns identification, the form, duplicate detection and the Case record. Specialist teams (technical, billing) own what happens after classification; this process ends where theirs begin.

## Process flow
1. The customer opens the case form in the portal. Determine whether the session is authenticated or a guest visit.
2. For an authenticated customer, use the Signed-In User Case Action; the contact and account are already known. For a guest, use the Guest User Case Action; require a solved verification challenge before continuing and collect the reporter's name, email and phone.
3. Present the case form fields configured on the relevant action's layout. Suggest Knowledge articles as the customer types the subject and description; let the customer continue to submission or resolve the question via an article.
4. Validate that all fields required by the layout are present. Request missing information; do not guess the affected service or category.
5. Search for an open Case from the same contact (or the same guest identity) against the same service and a similar category. For a confirmed duplicate, link the new contact to the existing Case instead of opening a second one.
6. Create the Case, set its Record Type from the selected category, and set the channel detail to distinguish authenticated and guest Experience Cloud submissions.
7. Send the customer a confirmation containing the Case number.
8. Route the Case by category: technical fault or quality concern continues in [Customer issues and faults](doc:BP-ISSUE); a disputed charge continues in [Billing complaints](doc:BP-BILL); a general inquiry is queued for handling directly from this Case.

## Rules
A guest submission never discloses another customer's data, even when the guest's details resemble an existing contact. Linking a contact to an existing Case never discards the new evidence (description, attachment) it carried. Classification recorded at registration may be corrected later by a specialist team; the correction is Case history, not a silent overwrite.

## References
[Case registration data model](doc:DATA-CASE) · [Solution design](doc:SD-CASEREG)
