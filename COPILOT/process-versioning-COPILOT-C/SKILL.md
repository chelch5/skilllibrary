---
name: process-versioning
description: Tracks workflow contract versions and defines how repo state should respond to a process upgrade. Trigger when a workflow process changes and existing tickets need migration. Do NOT use for code versioning (use semver/git for that).
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agentic-orchestration-and-autonomy
  priority: P2
  maturity: draft
  risk: low
  tags: [versioning, process, migration]
---

# Purpose
Maintains version history for workflow contracts and provides migration procedures when the process definition changes.

# When to use this skill
Use when:
- A workflow process is being updated and existing in-flight work needs to be migrated
- Auditing the history of how a process evolved

Do NOT use when:
- Managing code or artifact versioning (use git and semver)
- The process is brand new with no prior version

# Operating procedure
1. Tag the current process version before making changes
2. Document what changed and why in a process changelog
3. Define a migration procedure for in-flight tickets under the old version
4. Run the migration and verify all tickets reference the new process version

# Output defaults
A process changelog entry with version number, change description, migration steps, and affected ticket IDs.

# Failure handling
If migration fails for any ticket, mark that ticket as blocked with a reference to the process version conflict. Do not silently skip.
