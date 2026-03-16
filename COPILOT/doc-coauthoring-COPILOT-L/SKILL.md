---
name: doc-coauthoring
description: Supports iterative co-writing of documents with staged drafts, review cycles, and revision discipline. Use when documents require multiple contributors or approval stages.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P2
  maturity: draft
  risk: low
  tags: [coauthoring, collaboration, documents, review]
---

# Purpose
Supports iterative co-writing of documents with staged drafts, review cycles, and revision discipline.

# When to use this skill
Use when:
- Managing multi-author document drafting and review cycles
- Structuring document versions with clear draft states
- Coordinating review and approval workflows for documents

Do NOT use when:
- Single-author documents with no review requirement
- Real-time collaborative editing (different tooling)

# Operating procedure
1. Define document stages (draft, review, approved)
2. Assign sections to authors with clear ownership
3. Collect and reconcile reviewer feedback
4. Track changes with versioned drafts
5. Publish final approved version

# Output defaults
Versioned document drafts with reviewer comments, change tracking, and approval status

# Failure handling
If reviewers conflict, escalate to document owner for resolution.
