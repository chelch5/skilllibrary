---
name: runbook-writing
description: Creates operational guides for setup, recovery, diagnosis, and routine procedures. Ensures repeatable execution without relying on tribal knowledge.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P1
  maturity: draft
  risk: low
  tags: [runbook, operations, procedures, sre]
---

# Purpose
Creates operational guides for setup, recovery, diagnosis, and routine procedures.

# When to use this skill
Use when:
- Writing a runbook for incident response or operational procedures
- Documenting deployment or recovery steps for a service
- Creating a step-by-step guide for routine operations

Do NOT use when:
- High-level architecture documentation (use spec-authoring)
- User-facing how-to guides (different audience)

# Operating procedure
1. Define trigger/purpose of runbook
2. List prerequisites and required access
3. Write numbered step-by-step procedure
4. Add validation checks between steps
5. Include escalation path and contacts

# Output defaults
Numbered runbook with steps, validations, prerequisites, and escalation paths

# Failure handling
If a step fails, document expected vs actual. Escalate if resolution exceeds 15 min.
