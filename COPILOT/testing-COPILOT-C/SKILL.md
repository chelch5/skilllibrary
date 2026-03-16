---
name: testing
description: "Chooses and structures appropriate testing layers for the current stack: unit, integration, e2e, snapshot, or property-based. Testing was explicitly identified as missing from current generated packs. Trigger when the task context clearly involves testing."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P0
  maturity: draft
  risk: low
  tags: [testing, unit, integration]
---

# Purpose
Chooses and structures appropriate testing layers for the current stack: unit, integration, e2e, snapshot, or property-based.

# When to use this skill
Use when:
- when the user or repo work clearly points at testing
- when a task in the "Generated Repo Core Skills" family needs repeatable procedure rather than ad hoc prompting
- when a plan, ticket, or repo state would benefit from explicit guardrails around testing

Do NOT use when:
- The task is unrelated to testing
- A simpler direct approach is sufficient without structured procedure

# Operating procedure
1. Keep the scope explicit. The name should not hide unrelated responsibilities.
2. Prefer references, scripts, examples, or evals when testing would otherwise become a vague checklist.
3. Decide whether this belongs in the always-generated core, a stack/profile pack, or the optional registry.

# Output defaults
Structured markdown artifact(s) committed to the repo or surfaced as a response, with clear next steps or follow-up items listed.

# Failure handling
If inputs are missing or ambiguous, surface the specific gap as a decision item rather than guessing. If the procedure cannot complete, document partial progress and blockers explicitly.
