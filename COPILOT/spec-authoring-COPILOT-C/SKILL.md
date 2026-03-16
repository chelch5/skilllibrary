---
name: spec-authoring
description: Turns ideas into formal specifications with goals, non-goals, constraints, interfaces, and acceptance signals. Use before implementation to align stakeholders on requirements.
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
  tags: [spec, specification, requirements, design]
---

# Purpose
Turns ideas into formal specifications with goals, non-goals, constraints, interfaces, and acceptance signals.

# When to use this skill
Use when:
- Writing a feature spec or design document before implementation
- Capturing requirements with explicit non-goals and constraints
- Defining acceptance criteria for a deliverable

Do NOT use when:
- Implementation work (use after spec is approved)
- Informal notes or exploratory thinking documents

# Operating procedure
1. Define purpose and problem statement
2. List goals and explicit non-goals
3. Specify interfaces, APIs, or data contracts
4. Define acceptance criteria and test signals
5. Add open questions and decision log

# Output defaults
Spec document with goals, non-goals, interfaces, constraints, and acceptance criteria

# Failure handling
If spec is too broad, split into sub-specs. Unresolved open questions block approval.
