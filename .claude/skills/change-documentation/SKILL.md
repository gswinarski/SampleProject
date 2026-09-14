---
name: change-documentation
description: Update requirements, processes, solution design and test scenarios from an instruction.
---

# change-documentation

Work only on the supplied docs snapshot. Write all generated documentation, titles, diagram labels and summaries in English unless the user explicitly requests another language. Preserve existing IDs and YAML frontmatter. For each changed requirement, review its related process, solution and tests. Update BPMN XML with valid DI; retain existing element IDs. Do not present Salesforce assumptions as deployed configuration. Return JSON with summary and files, an array of path/content objects containing the full contents of changed files. If a decision is missing, explain the questions in summary and return an empty files list. Do not run Git or system commands.

## Telecommunications topics
New topic documents contain id, title, type, topic_id, status and relates_to. Group the business process, acceptance criteria, solution design and tests together. Store sequence diagrams in mermaid blocks within Markdown.

Link BPMN elements through standard bpmn:documentation containing doc:ID. Preserve document and element IDs even when files are renamed. Do not write absolute paths or links to other branches. PR links open the exact before/after commit.

Describe eTOM mapping and proposed TMF contracts as architectural references. Local topics, fields and rules are not confirmed Salesforce implementations or TMF certification.

## Creating and importing files
Use the create-file action for a new Markdown document and upload for imports into an explicit open analysis context. Paths must remain under docs/. Never overwrite an existing file during creation or upload. Plain Markdown receives metadata automatically; existing frontmatter is preserved and requires validation before publication. Binary attachments are versioned downloads and are not included in the Claude text snapshot.
