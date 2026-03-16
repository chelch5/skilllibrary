---
name: solidjs-patterns
description: Captures SolidJS-specific reactive patterns, component structure, and signal conventions as a frontend seed. Use when building applications with SolidJS.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: external-reference-seeds
  priority: P2
  maturity: draft
  risk: low
  tags: [solidjs, frontend, reactive, javascript]
---

# Purpose
Captures SolidJS-specific reactive patterns, component structure, and signal conventions as a frontend seed.

# When to use this skill
Use when:
- Building or refactoring components in SolidJS
- Implementing reactive state with SolidJS signals and stores
- Applying SolidJS-specific patterns (createSignal, createMemo, createEffect)

Do NOT use when:
- React or other non-SolidJS frameworks
- Server-side rendering without SolidJS Start

# Operating procedure
1. Structure components with SolidJS signal-based reactivity
2. Use createSignal for local state, createStore for complex state
3. Apply createMemo for derived values
4. Avoid accessing signals outside reactive context
5. Test with solid-testing-library

# Output defaults
SolidJS component files with correct signal usage, store patterns, and effect handling

# Failure handling
If reactivity breaks, verify signal is accessed inside reactive context. Avoid closures.
