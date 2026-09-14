---
name: publish-changes
description: Publish a change set for local review.
---

# publish-changes

Call publish. The code validates, commits docs, updates the base and pushes the branch. A local change request is not a GitHub PR. Preserve the analysis on conflict and explain next steps.

Complete analysis publishes only the analysis specified by context and marks it as awaiting review. Refreshing a PR supersedes only the previous open PR for that analysis. Other analyses and their PRs remain open.
