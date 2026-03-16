---
name: skill-lifecycle-management
description: "Manages skill creation, rollout, revision, deprecation, and archival states over time. A durable library needs a lifecycle, not just a creation phase. Trigger when the task context clearly involves skill lifecycle management."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: meta-skill-engineering
  priority: P1
  maturity: draft
  risk: low
  tags: [lifecycle, management, states]
---

# Purpose
Manages a skill through its full lifecycle: from initial creation through active use, revision, deprecation, and eventual archival — ensuring the library stays coherent and that retired skills do not silently break dependent workflows.

# When to use this skill
Use when:
- The user says "manage the lifecycle of this skill", "what state is this skill in?", or "how do we retire this skill properly?"
- A library audit has produced lifecycle actions (from `skill-catalog-curation`) that need to be executed
- A skill is being promoted, revised, or retired and the lifecycle state needs to be updated correctly
- A long-running project needs to track which skills are active, deprecated, or archived

Do NOT use when:
- The user wants to deprecate one specific skill (use `skill-deprecation-manager` for that focused workflow)
- The user wants to author a new skill (use `skill-authoring`)
- The library has fewer than 15 skills — lightweight lifecycle tracking is sufficient (just a `maturity` field)

# Operating procedure
1. **Define the lifecycle states** for the library (customise if the library has different conventions):
   - `draft`: Being written, not yet validated — do not rely on in production
   - `beta`: Validated for basic use cases, accepting feedback — use with monitoring
   - `stable`: Validated, promoted, default choice for new installations
   - `deprecated`: Replaced by a newer skill or no longer recommended — still functional but do not use for new work
   - `archived`: Removed from active library, kept for reference only — do not install
2. **Audit current states**: List every skill with its current maturity field. Flag inconsistencies (skills that have been in `draft` for more than 2 release cycles, skills in `stable` with known bugs)
3. **Apply promotion criteria**: A skill moves from `draft` → `beta` when: it has been tested with at least 3 real prompts and passed. From `beta` → `stable` when: it has been evaluated (from `skill-evaluation`) with a "Promote" verdict
4. **Apply deprecation criteria**: A skill should be deprecated when: a better replacement exists, or it has not been used in 3+ release cycles, or it consistently fails evaluation
5. **Execute state transitions**: For each skill being transitioned, update the `metadata.maturity` field in frontmatter and add a lifecycle event to `PROVENANCE.md` (or create one)
6. **Notify dependent workflows**: If a skill being deprecated is referenced in AGENTS.md, commands, or other skills, flag those references as needing update
7. **Update the library index**: Reflect the new states in any catalog or index file

# Output defaults
A **Lifecycle Audit** table (skill | current state | recommended state | reason), a list of **State Transitions to Execute**, and a **Dependency Impact** list for any skill being deprecated.

# Failure handling
If lifecycle states are not currently tracked in frontmatter, add the `maturity` field to all skills based on best-available evidence before proceeding with lifecycle management.
