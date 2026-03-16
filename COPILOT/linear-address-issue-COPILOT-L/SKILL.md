---
name: linear-address-issue
description: A Linear-specific skill for resolving, updating, and closing issues cleanly following Linear workflow conventions. Use when working on tasks tracked in Linear.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: external-reference-seeds
  priority: P2
  maturity: draft
  risk: low
  tags: [linear, project-management, issue-tracking, workflow]
---

# Purpose
A Linear-specific skill for resolving, updating, and closing issues cleanly following Linear workflow conventions.

# When to use this skill
Use when:
- Resolving or updating a Linear issue during development
- Following Linear workflow states (backlog, in progress, done)
- Linking code changes to Linear issues

Do NOT use when:
- Non-Linear project management tools (use appropriate skill)
- General task management without Linear

# Operating procedure
1. Read issue description and acceptance criteria
2. Update issue status to In Progress
3. Implement changes per issue requirements
4. Link commits or PRs to issue using Linear magic words
5. Update issue with completion notes and mark Done

# Output defaults
Updated Linear issue with status, linked commits/PRs, and completion notes

# Failure handling
If issue requirements are unclear, comment on the issue before implementing.
