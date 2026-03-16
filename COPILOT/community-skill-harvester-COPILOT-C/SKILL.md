---
name: community-skill-harvester
description: "Finds external skills, extracts reusable patterns, and converts them into local proposal candidates. Your reports rely heavily on external examples, so harvesting should be formalized. Trigger when the task context clearly involves community skill harvester."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P2
  maturity: draft
  risk: low
  tags: [community, harvesting, import]
---

# Purpose
Finds external skills, extracts reusable patterns, and converts them into local proposal candidates.

# When to use this skill
Use when:
- when creating, adapting, refining, installing, testing, or packaging a skill
- when a task in the "Package Scaffolding Skills" family needs repeatable procedure rather than ad hoc prompting
- when a plan, ticket, or repo state would benefit from explicit guardrails around community skill harvester

Do NOT use when:
- The task is unrelated to community skill harvester
- A simpler direct approach is sufficient without structured procedure

# Operating procedure
1. Keep the scope explicit. The name should not hide unrelated responsibilities.
2. Prefer references, scripts, examples, or evals when community skill harvester would otherwise become a vague checklist.
3. Decide whether this belongs in the always-generated core, a stack/profile pack, or the optional registry.

# Output defaults
Structured markdown artifact(s) committed to the repo or surfaced as a response, with clear next steps or follow-up items listed.

# Failure handling
If inputs are missing or ambiguous, surface the specific gap as a decision item rather than guessing. If the procedure cannot complete, document partial progress and blockers explicitly.
