---
name: project-context
description: "Loads the repo's source-of-truth documents in a deterministic order before planning or editing. This is one of the strongest existing generated skills and should stay. Trigger when the task context clearly involves project context."
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
  tags: [context, loading, navigation]
---

# Purpose
Load the project's canonical context documents in a deterministic order so every agent session starts correctly oriented — no re-discovery, no stale assumptions.

# When to use this skill
Use when:
- An agent is starting a new session on a project it should already know
- A context switch has occurred (different repo, different feature branch, different agent)
- An agent is about to make architectural decisions and needs to confirm current project state
- The user says "reload context", "remind yourself of the project", or "what do we know about X?"

Do NOT use when:
- Context is already loaded and confirmed current in this session
- The project has no canonical context documents (use repo-scaffold-factory first)

# Operating procedure
Load documents in this exact order (stop if a document is missing and flag it):

1. **`AGENTS.md`** — stack rules, agent roles, managed surfaces, forbidden actions
2. **`docs/specs/BRIEF.md`** (or equivalent canonical brief) — what the project is, goals, constraints
3. **`tickets/BOARD.md`** — current work state: what is done, in progress, and pending
4. **`tickets/MANIFEST.json`** — machine-readable ticket state for dependency checking
5. **`.opencode/agents/`** — active agent definitions and their scopes
6. **Any `docs/adr/*.md` files** created in the last 7 days — recent architectural decisions

After loading, emit a context confirmation block:
```
PROJECT: <name>
BRIEF_HASH: <first 8 chars of brief sha or last-modified date>
OPEN_TICKETS: <count> (<P0 count> P0, <P1 count> P1)
CURRENT_FOCUS: <ticket ID and title of in-progress work>
LAST_DECISION: <most recent ADR title>
BLOCKERS: <list or "none">
```

# Output defaults
Context confirmation block. Do not summarize every document — emit only the structured block above.

# Failure handling
If a required document is missing, log `MISSING: <document>` in the context block and do not proceed until the gap is acknowledged. Do not invent context from memory.
