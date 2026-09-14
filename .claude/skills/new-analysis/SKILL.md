---
name: new-analysis
description: Start an analysis on an isolated branch.
---

# new-analysis

Collect a name and goal. Call new. The tool synchronizes main and creates a worktree. Success: an active analysis with a base commit.

Multiple analyses may remain open. Each has its own ID and worktree. Create new analyses from current main regardless of the selected view. Switching views neither changes files nor completes other analyses.

The user interface starts every selected workspace in the searchable file browser. Switching clears file tabs only after unsaved drafts are saved or explicitly discarded; cancelling keeps the current workspace and drafts.
