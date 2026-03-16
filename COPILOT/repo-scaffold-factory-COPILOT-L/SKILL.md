---
name: repo-scaffold-factory
description: "Generates the mechanical repository structure, starter files, and managed surfaces from the canonical brief. This keeps repetitive file-tree work deterministic and scriptable. Trigger when the task context clearly involves repo scaffold factory."
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
  tags: [scaffolding, repo, generation]
---

# Purpose
Generate the base repository file structure — README, AGENTS.md, docs layout, .opencode/ config, CI skeleton, and managed surfaces — from a canonical brief.

# When to use this skill
Use when:
- A greenfield repository is being created and needs its initial structure
- The user says "scaffold this project", "set up the repo", or "generate the base structure"
- A canonical brief or spec-pack exists and needs to be translated into files
- An existing repo is missing standard managed surfaces (no AGENTS.md, no .opencode/, etc.)

Do NOT use when:
- The repo already has all managed surfaces and only needs content updates
- The request is about scaffolding a specific feature, not the overall repo structure

# Operating procedure
1. **Confirm brief**: read the canonical brief (or run spec-pack-normalizer first if missing)
2. **Detect stack**: run stack-profile-detector to determine language, framework, and cloud target
3. **Generate the file tree**:
   ```
   README.md               ← project overview, setup instructions, links to AGENTS.md
   AGENTS.md               ← agent operating rules, stack conventions, managed surfaces list
   .opencode/
     agents/               ← one .md file per agent role
     commands/             ← slash command definitions
     skills/               ← project-local skill overrides
     tools/                ← tool manifests
   docs/
     adr/                  ← architecture decision records
     specs/                ← canonical brief and design docs
   tickets/                ← ticket system (use ticket-pack-builder)
   .github/
     workflows/            ← CI skeleton
   ```
4. **Write each file** with real content, not placeholders. README must have actual setup steps. AGENTS.md must have actual stack rules.
5. **Validate**: check that all cross-references between files are correct (e.g., AGENTS.md mentions docs that exist)

# Output defaults
Complete file tree committed to the repo. Every file must have real content — "TODO: fill in" is not acceptable output.

# Failure handling
If the brief is insufficient to fill a section, leave a `<!-- MISSING: description of what's needed -->` HTML comment in that section and log it as a follow-up item.
