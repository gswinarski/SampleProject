---
id: DATA-CONTACT
title: Contact — data model
type: data-object
topic_id: PROJECT
status: draft
relates_to:
- SD-CASEREG
---

# Contact — data model

Only the fields [Case registration](doc:TOPIC-CASEREG) relies on for identification. See [[../README|data model conventions]].

## Standard fields

### Id
Standard. Referenced from [[salesforce-case#ContactId]] when the Signed-In User Case Action creates a Case for an authenticated visitor.

### AccountId
Standard, lookup to Account. Links the Contact to [[salesforce-account]]; the pair together identify the customer on a registered Case.

### Email
Standard. Used to reconcile a guest submission ([[salesforce-case#SuppliedEmail]]) to a known Contact, when that reconciliation is in scope — see the open decisions in [Solution design](doc:SD-CASEREG).

### Phone
Standard. Same role as [[salesforce-contact#Email]] for phone-based reconciliation.
