---
name: release-engineering
description: "Coordinates tag, changelog, package, artifact, release-note, and verification steps for shipping work. Useful for repos that turn into packages or products. Trigger when the task context clearly involves release engineering."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P1
  maturity: draft
  risk: low
  tags: [release, changelog, packaging]
---

# Purpose
Coordinates tag, changelog, package, artifact, release-note, and verification steps for shipping work.

# When to use this skill
Use when:
- when the user or repo work clearly points at release engineering
- when a task in the "Generated Repo Core Skills" family needs repeatable procedure rather than ad hoc prompting
- when a plan, ticket, or repo state would benefit from explicit guardrails around release engineering

Do NOT use when:
- The task is unrelated to release engineering
- A simpler direct approach is sufficient without structured procedure

# Operating procedure
1. Keep the scope explicit. The name should not hide unrelated responsibilities.
2. Prefer references, scripts, examples, or evals when release engineering would otherwise become a vague checklist.
3. Decide whether this belongs in the always-generated core, a stack/profile pack, or the optional registry.

# Output defaults
Structured markdown artifact(s) committed to the repo or surfaced as a response, with clear next steps or follow-up items listed.

# Failure handling
If inputs are missing or ambiguous, surface the specific gap as a decision item rather than guessing. If the procedure cannot complete, document partial progress and blockers explicitly.
