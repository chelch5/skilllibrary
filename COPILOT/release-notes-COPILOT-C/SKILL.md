---
name: release-notes
description: Writes useful release notes that summarize what changed, who is affected, and what to verify. Translates technical changes into audience-appropriate communication.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P2
  maturity: draft
  risk: low
  tags: [release-notes, changelog, versioning, communication]
---

# Purpose
Writes useful release notes that summarize what changed, who is affected, and what to verify.

# When to use this skill
Use when:
- Writing release notes for a software release
- Generating a changelog from commit history
- Communicating breaking changes to users or stakeholders

Do NOT use when:
- Internal code comments or PR descriptions
- Detailed technical implementation docs

# Operating procedure
1. Collect changes from commits/PRs since last release
2. Categorize as features, fixes, breaking changes, deprecations
3. Write audience-appropriate summary for each change
4. Highlight breaking changes and migration steps
5. Review with stakeholder before publishing

# Output defaults
Structured release notes with categories (features, fixes, breaking changes, deprecations)

# Failure handling
If commits are ambiguous, ask developer for intent. Never guess breaking change impact.
