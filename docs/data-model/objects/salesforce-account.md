---
id: DATA-ACCOUNT
title: Account — data model
type: data-object
topic_id: PROJECT
status: draft
relates_to:
- SD-CASEREG
---

# Account — data model

Only the fields [Case registration](doc:TOPIC-CASEREG) relies on for identification. See [[../README|data model conventions]]. Whether the target org uses standard Business Accounts, Person Accounts, or both is an open decision noted in [Architecture](doc:PROJECT-ARCH); this note does not assume either.

## Standard fields

### Id
Standard. Referenced from [[salesforce-case#AccountId]] for an authenticated customer's Case.

### Name
Standard. Displayed back to the customer and to the agent picking up a registered Case; for a Person Account this is derived from the person's name rather than entered directly.
