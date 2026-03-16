---
name: handoff-brief
description: "Builds a concise restart surface with actual state, next steps, and reading order. Long-running or interrupted work needs a compact re-entry surface. Trigger when the task context clearly involves handoff brief."
source: github.com/scafforge/session
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P0
  maturity: draft
  risk: low
  tags: [handoff, context, restart]
---

# Purpose
Builds a concise restart surface with actual state, next steps, and reading order.

# When to use this skill
Use when:
- when the user or repo work clearly points at handoff brief
- when a task in the "Package Scaffolding Skills" family needs repeatable procedure rather than ad hoc prompting
- when a plan, ticket, or repo state would benefit from explicit guardrails around handoff brief

Do NOT use when:
- The task is unrelated to handoff brief
- A simpler direct approach is sufficient without structured procedure

# Operating procedure
1. Keep the scope explicit. The name should not hide unrelated responsibilities.
2. Prefer references, scripts, examples, or evals when handoff brief would otherwise become a vague checklist.
3. Decide whether this belongs in the always-generated core, a stack/profile pack, or the optional registry.

# Output defaults
Structured markdown artifact(s) committed to the repo or surfaced as a response, with clear next steps or follow-up items listed.

# Failure handling
If inputs are missing or ambiguous, surface the specific gap as a decision item rather than guessing. If the procedure cannot complete, document partial progress and blockers explicitly.
