---
name: scaffold-kickoff
description: "Entry point that coordinates end-to-end repo scaffolding from messy inputs to a usable generated repository. This is the top-level conductor for the whole scaffold chain and should remain explicit rather than implicit. Trigger when the task context clearly involves scaffold kickoff."
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
  tags: [scaffolding, kickoff, orchestration]
---

# Purpose
Orchestrates the full spec-to-repo kickoff flow for greenfield or early-stage projects. This skill sequences five distinct phases—spec normalization, stack detection, repo structure generation, ticket decomposition, and agent team bootstrap—ensuring each phase completes with verifiable artifacts before the next begins.

# When to use this skill
Use when:
- Starting a new project from specs, planning docs, chat transcripts, or rough requirements
- Bootstrapping an agent-operated repo that needs AGENTS.md, ticket system, and skill infrastructure
- Converting an existing prototype into a properly scaffolded, agent-ready repository

Do NOT use when:
- Adding features to an already-scaffolded repo (use ticket-execution instead)
- Only normalizing specs without generating structure (use spec-pack-normalizer)
- The repo already has a functioning ticket system and agent layer

# Operating procedure
1. **Collect inputs**: Gather all source material—specs, notes, chat logs, reference repos, design docs. Place in a staging area (e.g., `_inputs/` or session workspace).

2. **Invoke spec-pack-normalizer**: Produce `docs/BRIEF.md` (canonical project summary), `docs/DECISIONS.md` (resolved questions), and `docs/CONSTRAINTS.md` (hard boundaries). Gate: all three files must exist.

3. **Invoke stack-profile-detector**: Analyze brief and any existing files to emit `docs/STACK-PROFILE.md` with language, framework, runtime, and cloud target. Gate: profile must be explicit, not "unknown".

4. **Invoke repo-scaffold-factory**: Generate base structure:
   - `README.md` with project name, quick-start, and pointer to AGENTS.md
   - `AGENTS.md` with reading order and agent instructions
   - `.github/` with issue templates and PR template
   - `docs/` skeleton with architecture placeholder
   - `.opencode/` or `.copilot/` agent configuration directory

5. **Invoke ticket-pack-builder**: Decompose brief into `tickets/` directory with:
   - `TICKET-INDEX.md` (manifest with IDs, titles, statuses)
   - `BOARD.md` (Kanban view)
   - Individual ticket files with acceptance criteria and dependencies

6. **Invoke opencode-team-bootstrap** (if applicable): Generate project-specific agents, tools, and skills in `.opencode/agents/`, `.opencode/skills/`.

7. **Final verification**: Run `tree -L 2` to confirm structure. Check that all gate files exist. Commit scaffold with message: `chore: initial scaffold from kickoff`.

# Output defaults
```
<project>/
├── README.md
├── AGENTS.md
├── docs/
│   ├── BRIEF.md
│   ├── DECISIONS.md
│   ├── CONSTRAINTS.md
│   └── STACK-PROFILE.md
├── tickets/
│   ├── TICKET-INDEX.md
│   ├── BOARD.md
│   └── TKT-001-*.md
├── .github/
│   ├── ISSUE_TEMPLATE/
│   └── pull_request_template.md
└── .opencode/ (or .copilot/)
    ├── agents/
    └── skills/
```

# References
- Anthropic Skills README: https://github.com/anthropics/skills
- GitHub template repositories: https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template

# Failure handling
- **Missing specs**: Stop and request minimum viable input (problem statement + target users + rough scope)
- **Ambiguous stack**: Emit stack profile with `confidence: low` flag and list alternatives; proceed with most likely choice but document uncertainty
- **Partial completion**: Commit whatever was generated with `WIP:` prefix; log which phase failed in `docs/SCAFFOLD-STATUS.md`
- **Conflicting constraints**: Surface as decision items in DECISIONS.md rather than making silent choices
