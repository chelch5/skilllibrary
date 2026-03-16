---
name: repo-navigation
description: "Explains which directories are canonical, derived, preserved, or operational inside the repo. Agents drift when they confuse generated surfaces with source material. Trigger when the task context clearly involves repo navigation."
source: github.com/gpttalker/opencode-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: generated-repo-core
  priority: P0
  maturity: draft
  risk: low
  tags: [navigation, repo, directories]
---

# Purpose
Orient an agent quickly in an unfamiliar codebase — identifying canonical source, generated surfaces, entry points, and key conventions before any editing begins.

# When to use this skill
Use when:
- An agent is starting work in a repo it has not seen before
- The task is in an unfamiliar subdirectory or service
- An agent is about to edit a file but is not certain whether it is source or generated
- The user asks "where is X implemented?", "how is this codebase organized?", or "what is the entry point?"

Do NOT use when:
- The agent already has a loaded map of the repo from earlier in the same session
- The task is fully self-contained in a single known file

# Operating procedure
1. **Read the top-level README and AGENTS.md** — these are the canonical orientation documents
2. **Map the directory tree** (max 2 levels deep): identify purpose of each top-level directory
3. **Classify each directory** as one of: source (human-authored), generated (do not edit directly), operational (tickets, logs, config), or test
4. **Find entry points**: main function, API router, CLI entrypoint, or equivalent for the stack
5. **Identify the test pattern**: where tests live, how to run them, what the coverage baseline is
6. **Check for managed surfaces**: note any files marked as generated (header comment, AGENTS.md listing, or .opencode/ config)
7. **Record the navigation map** in a compact format before proceeding:
   ```
   src/         → source (TypeScript, entry: src/index.ts)
   generated/   → generated (do not edit)
   tickets/     → operational
   tests/       → test (run: npm test)
   ```

# Output defaults
Compact navigation map emitted before starting the actual task. Takes less than 60 seconds; do not deep-read all files.

# Failure handling
If README is missing or outdated, infer structure from file patterns. If a directory's classification is ambiguous, default to treating it as source (conservative) and flag it for clarification.
