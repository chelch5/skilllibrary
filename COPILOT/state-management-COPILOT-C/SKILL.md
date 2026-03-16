---
name: state-management
description: Chooses and structures local, server cache, and global state patterns to avoid unnecessary complexity. Trigger when designing state architecture for a web app. Do NOT use for backend state or database design.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P1
  maturity: draft
  risk: low
  tags: [state-management, react, frontend]
---

# Purpose
Guides the selection and structure of state management patterns—local, server cache, and global—to avoid over-engineering and state drift.

# When to use this skill
Use when:
- Designing the state architecture for a new or growing web application
- Diagnosing state-related bugs such as stale data or unnecessary re-renders

Do NOT use when:
- Managing backend or database state
- State is simple enough to use useState alone

# Operating procedure
1. Classify each piece of state: local UI state, server cache, global shared state
2. Use useState/useReducer for local state; TanStack Query or SWR for server cache
3. Reach for a global store (Zustand, Jotai) only when state truly needs to be shared across many unrelated components
4. Avoid prop drilling beyond two levels by using context or a global store
5. Document state ownership and mutation rules to prevent concurrent modification bugs

# Output defaults
A state architecture decision record with state classification, library choices, and ownership rules.

# Failure handling
If state becomes inconsistent, identify the mutation source and add explicit state transition logging before investigating further.
