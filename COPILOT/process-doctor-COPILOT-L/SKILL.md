---
name: process-doctor
description: "Runs a repo-local process repair or verification pass after workflow changes. This is the generated-repo counterpart to the package-level repair skill. Trigger when the task context clearly involves process doctor."
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
  tags: [process, repair, verification]
---

# Purpose
Run a local process repair pass on a repo's generated operating layer after workflow changes — verifying that agents, commands, tickets, and skills are internally consistent.

# When to use this skill
Use when:
- A workflow upgrade has been applied and the operating layer needs verification
- Agents are routing incorrectly or hitting unexpected errors on known commands
- AGENTS.md was edited but dependent files were not updated
- The user says "something in the workflow is broken" or "agents aren't following the process"

Do NOT use when:
- The issue is in application code, not in the operating layer
- The repo has never had an operating layer (use repo-scaffold-factory)
- A full audit is needed (use repo-process-doctor which is more comprehensive)

# Operating procedure
1. **Diff the operating layer against last known good state**: `git diff HEAD~1 -- AGENTS.md .opencode/ tickets/MANIFEST.json`
2. **Run the five consistency checks**:
   - Agent files referenced in AGENTS.md all exist at their stated paths
   - Command files in `.opencode/commands/` reference agents that exist
   - Skill names in `.opencode/skills/` match installed skill filenames
   - Ticket MANIFEST.json matches ticket file statuses on disk
   - BOARD.md column counts match MANIFEST.json status counts
3. **For each inconsistency**: propose the minimal fix (rename, update reference, or regenerate file)
4. **Apply fixes** that are unambiguous (path corrections, stale references)
5. **Flag fixes** that require judgment (conflicting states, missing files that need new content)
6. **Re-run checks** after applying fixes to confirm consistency

# Output defaults
Pass/fail result for each check + list of applied and flagged fixes. Emit as a repair log, not prose.

# Failure handling
If a check cannot be evaluated (e.g., no git history), run it against current state only and note the limitation.
