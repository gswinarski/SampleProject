# Documentation map

Start here — this is the fastest way for a human or an AI assistant to find how something works and what it depends on.

## Shared context
`project/` holds context that applies to every analysis: [overview](project/overview.md), [architecture](project/architecture.md), [glossary](project/glossary.md), [TM Forum mapping](project/tmf-mapping.md). Read these first for the boundaries and vocabulary the rest of the docs assume.

## Business analyses (current convention)
Under `operations/<eTOM area>/<eTOM subprocess>/<topic>/`, one folder per business topic, always the same five documents plus diagrams:
- `index.md` — hub: links to the other four, the diagrams, and sources/limitations.
- `business-process.md` — purpose, actors, numbered process flow, rules.
- `acceptance-criteria.md` — a Given/When/Then table.
- `solution-design.md` — component responsibilities, data model, open decisions.
- `test-scenarios.md` — a UAT table keyed to the acceptance criteria.
- `diagrams/*.bpmn` — collaboration + lanes; every meaningful element carries a `bpmn:documentation` back-link to the markdown that explains it.
- optional `steps/` (one file per BPMN task worth a deep dive) and `integrations/<name>/{contract.md, sequence.md}` (one per external system call; sequence diagrams are Mermaid, not BPMN).

Every document has YAML frontmatter (`id, title, type, topic_id, status, relates_to`) and cross-links other documents with a `doc:ID` reference (for example `[Business process](doc:BP-ISSUE)`), never a relative markdown link or an absolute path. To find what a change impacts, search for the `id` being changed and for every `doc:<that id>` reference to it.

Current topics: [customer issues and faults](operations/assurance/customer-problem-management/customer-issue-handling/index.md), [billing complaints](operations/billing-and-revenue-management/customer-bill-inquiry-handling/billing-complaint/index.md), [address and FTTH qualification](operations/fulfillment/service-configuration-and-activation/address-and-service-qualification/index.md), [Case registration via Experience Cloud](operations/customer-relationship-management/customer-interface-management/case-registration/index.md) — the shared front door the other three build on.

## Data model
`data-model/` documents the Salesforce objects/fields the analyses above depend on, one file per object under `data-model/objects/`. See [data-model/README.md](data-model/README.md) for the full convention. In short: object notes are `doc:ID` citizens like any other document, and individual fields are linked at the heading level with Obsidian wikilinks (`[[salesforce-case#Registration_Channel_Detail__c]]`), so both Obsidian's backlinks pane and a plain `grep` can answer "which processes use this field."

## Plans
`plans/telco-00X.md` — one short plan per analysis (goal, steps, completion criteria), created when the analysis branch opens.

## Older, simpler example
`processes/`, `requirements/`, `solution/`, `tests/` hold a small, standalone Lead/Case example (one object per file, minimal frontmatter with `PROC-/REQ-/SOL-/TEST-` ids). It is not superseded by the `operations/` convention above — it is a different, coarser granularity kept for illustration — but it is unrelated to the telco topics and does not share ids or data-model links with them.

## Everything is one Obsidian vault
The whole `docs/` tree opens as a single Obsidian vault (see the repo root). `doc:ID` and `[[wikilink]]` are two different, complementary schemes: `doc:ID` is resolved by tooling (and validated by `check-documentation`) for whole-document relationships; `[[object#field]]` is a native Obsidian link for field-level relationships. Both are plain text and both are `grep`-able even without Obsidian.
