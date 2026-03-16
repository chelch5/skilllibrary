---
name: svelte
description: Applies Svelte component, store, and routing patterns for Svelte/SvelteKit projects. Trigger when building or reviewing a Svelte or SvelteKit application. Do NOT use for React or Vue projects.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P2
  maturity: draft
  risk: low
  tags: [svelte, sveltekit, frontend]
---

# Purpose
Provides Svelte-specific component, reactive store, and SvelteKit routing patterns for building performant web applications.

# When to use this skill
Use when:
- Building a new application in Svelte or SvelteKit
- Reviewing Svelte code for idiomatic patterns and performance

Do NOT use when:
- Working in React (use react-typescript) or Vue (use vue)
- General frontend patterns applicable to any framework

# Operating procedure
1. Structure components with clear script/markup/style separation
2. Use Svelte reactive statements (`$:`) and stores for state management
3. Use SvelteKit's file-based routing and load functions for data fetching
4. Prefer server-side rendering where possible using SvelteKit's SSR
5. Use Svelte's transition and animation primitives for UI interactions

# Output defaults
Svelte components with reactive state, SvelteKit route files with load functions, and store definitions.

# Failure handling
If a reactive statement creates a circular dependency, refactor it into explicit event handlers and derived stores.
