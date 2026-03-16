---
name: gap-analysis
description: "Compares current repo or plan state against target state and lists missing pieces cleanly. Useful during retrofits and scaffold review. Trigger when the task context clearly involves gap analysis."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: planning-review-and-critique
  priority: P1
  maturity: draft
  risk: low
  tags: [gaps, analysis, comparison]
---

# Purpose
Compares a current state (repo, plan, codebase, process) against a desired target state and produces an explicit inventory of what is missing, incomplete, or wrong.

# When to use this skill
Use when:
- The user says "what's missing?", "gap analysis", or "what do we still need to do?"
- A scaffold has been generated and needs to be audited against requirements
- A repo is being retrofitted to meet a new standard or pattern
- A plan exists but it is unclear what has been implemented versus what remains

Do NOT use when:
- The user wants drift between a spec and code (use `drift-detection` — which has an authoritative reference)
- The user wants to understand why something failed (use `root-cause-analysis`)
- Both current and target states are the same — there are no gaps

# Operating procedure
1. **Define the current state**: Inventory what actually exists. For a repo: list files, modules, agents, tools, docs. For a plan: list completed milestones, resolved decisions, implemented features
2. **Define the target state**: Identify the authoritative description of what should exist. This could be: a requirements doc, a scaffold spec, a standard pattern, or the user's stated goal
3. **Map current to target**: For each item in the target state, check whether it exists in the current state. Status: Present / Partial / Absent
4. **Identify surplus items**: Things that exist in the current state but are NOT in the target state. Flag as: expected addition, potential scope creep, or legacy to remove
5. **Classify each gap**:
   - **Structural gap**: Missing file, module, or component
   - **Behavioural gap**: Component exists but does not behave as required
   - **Quality gap**: Exists and behaves correctly but does not meet the quality bar (incomplete tests, missing docs, poor error handling)
   - **Dependency gap**: A gap that blocks other items from being filled
6. **Prioritise the gaps**: Order by: dependency gaps first, then structural, then behavioural, then quality
7. **Estimate effort for each gap**: Small (< 1 day), Medium (1–3 days), Large (> 3 days)

# Output defaults
A gap inventory table (item | target state | current state | gap type | effort estimate), a **Dependency Gaps First** section, and a **Recommended Fill Order** list.

# Failure handling
If the target state is not defined, this skill cannot operate. Ask for the target reference before proceeding. If partial, complete the analysis only for the defined portion and state what is missing.
