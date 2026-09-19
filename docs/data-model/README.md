# Data model notes

This folder documents the Salesforce objects and fields referenced by the analyses under `docs/operations/`. It exists so that a field's meaning is written once, and every process that depends on it links to that one place instead of restating it.

## Where notes live
One file per object, under `objects/`, named `salesforce-<object>.md` (for example `salesforce-case.md`). The `salesforce-` prefix is deliberate: `docs/processes|requirements|solution|tests/` already contains an unrelated, older `case.md`/`lead.md` pair (a simpler Lead/Case demo), and this repository is one Obsidian vault — two files with the same basename would make `[[wikilinks]]` ambiguous. Non-Salesforce systems, if ever documented here, should get their own prefix (`oss-...`, `billing-...`) for the same reason.

## Frontmatter
Object notes carry the same frontmatter as every other document (`id`, `title`, `type: data-object`, `topic_id: PROJECT`, `status`, `relates_to`), so they are ordinary `doc:ID` citizens: a business-process or solution-design document can link to a whole object note with `doc:DATA-CASE` exactly as it would link to any other document.

## Field-level linking
Within an object note, every field is its own heading (`### FieldApiName`), using the exact API name. Any other document that depends on a specific field links to it with an Obsidian heading wikilink, for example:

```
[[salesforce-case#Registration_Channel_Detail__c]]
```

This gives two independent, complementary ways to discover dependencies:
- **Obsidian's backlinks pane**, for a human analyst opening `salesforce-case.md` and asking "who uses this field."
- **A plain-text search**, for any tool or AI that does not run inside Obsidian: `grep -r "salesforce-case#Registration_Channel_Detail__c" docs/` finds every consumer with no index to keep in sync.

Object notes deliberately do **not** maintain their own "referenced by" list. A hand-maintained list rots the moment a process changes and forgets to update it; a search does not. This mirrors the `impact-analysis` skill's own approach — compute dependencies on demand, and never claim the result is exhaustive.

## Standard vs. proposed fields
Every field is marked either **Standard** (a real Salesforce field, factual, not project-specific) or **Proposed (custom)** (a design suggestion for this project, using the `__c` suffix convention, not a claim that it exists in any org). Where a proposed field is inspired by a TM Forum attribute, the note says so and names the API/attribute — as an architectural reference, not a certified mapping.

## Current notes
- [[salesforce-case]] — the Case object, as extended for [Case registration](doc:TOPIC-CASEREG)
- [[salesforce-account]] — the Account fields Case registration relies on for customer identification
- [[salesforce-contact]] — the Contact fields Case registration relies on for customer identification
- [[salesforce-premise]] — a proposed custom object holding aggregated address coverage, used by [Postal-code address lookup and coverage check](doc:TOPIC-COVERAGE)
- [[salesforce-lead]] — the Lead fields that same process writes for an out-of-coverage address

Conceptual design for a fictional FTTH operator. Standard fields are verified against the Salesforce object reference; proposed fields and TMF mappings require agreement with the operator before implementation.
