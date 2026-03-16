---
name: isolation-guidance
description: "Chooses when work should use in-place edits versus worktrees, temp copies, or isolated lanes. Helps prevent one large change from clobbering unrelated work. Trigger when the task context clearly involves isolation guidance."
source: github.com/gpttalker/opencode-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P1
  maturity: draft
  risk: low
  tags: [isolation, worktrees, safety]
---

# Purpose
Chooses when work should use in-place edits versus worktrees, temp copies, or isolated lanes.

# When to use this skill
Use when:
- when the user or repo work clearly points at isolation guidance
- when a task in the "Generated Repo Core Skills" family needs repeatable procedure rather than ad hoc prompting
- when a plan, ticket, or repo state would benefit from explicit guardrails around isolation guidance

Do NOT use when:
- The task is unrelated to isolation guidance
- A simpler direct approach is sufficient without structured procedure

# Operating procedure
1. Keep the scope explicit. The name should not hide unrelated responsibilities.
2. Prefer references, scripts, examples, or evals when isolation guidance would otherwise become a vague checklist.
3. Decide whether this belongs in the always-generated core, a stack/profile pack, or the optional registry.

# Output defaults
Structured markdown artifact(s) committed to the repo or surfaced as a response, with clear next steps or follow-up items listed.

# Failure handling
If inputs are missing or ambiguous, surface the specific gap as a decision item rather than guessing. If the procedure cannot complete, document partial progress and blockers explicitly.
