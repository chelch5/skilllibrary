---
name: repo-process-doctor
description: "Audits the generated operating layer and repairs or replaces managed surfaces after process upgrades. You asked for a true repair path for sweeping repo changes; this is central. Trigger when the task context clearly involves repo process doctor."
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
  tags: [repair, process, audit]
---

# Purpose
Audit a repo's agent workflow layer for drift — contradictory status semantics, stale managed surfaces, broken routing, or raw-file stage control — and produce a prioritized repair plan.

# When to use this skill
Use when:
- Agents are producing incorrect or inconsistent outputs that suggest process drift
- The ticket board is out of sync with actual work state
- AGENTS.md or .opencode/ config was last updated more than one major workflow change ago
- A repo was forked or migrated and the operating layer was carried over unchanged
- The user says "something is broken with how the agents work" or "tickets aren't tracking correctly"

Do NOT use when:
- The issue is a bug in the code, not in the agent workflow (use a debugging approach)
- The repo has no agent workflow layer yet (use repo-scaffold-factory)

# Operating procedure
1. **Inventory the operating layer**: list all files in AGENTS.md, .opencode/agents/, .opencode/commands/, tickets/, and any referenced docs
2. **Check for the five drift patterns**:
   - **Status contradiction**: ticket status in MANIFEST.json disagrees with ticket file status
   - **Raw-file stage control**: stage tracked in prose instead of a structured field
   - **Dead agent references**: AGENTS.md references agent files that do not exist
   - **Stale skill list**: skills listed in .opencode/ that are not installed or are outdated
   - **Broken command routing**: slash commands reference agents or tools that no longer exist
3. **For each finding**: record file path, line number, pattern type, and proposed fix
4. **Prioritize repairs**: P0 = breaks ticket execution, P1 = causes incorrect agent behavior, P2 = cosmetic drift
5. **Emit the repair plan** in a structured table: `FILE | LINE | DRIFT_TYPE | REPAIR_ACTION`
6. Apply P0 fixes immediately; present P1/P2 for confirmation

# Output defaults
Repair plan table + immediate application of P0 fixes. Commit message must list each fixed item.

# Failure handling
If a managed surface is so stale it cannot be repaired incrementally, flag it for full regeneration via repo-scaffold-factory rather than patching line by line.
