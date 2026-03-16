---
name: vue
description: Applies Vue 3 Composition API, Pinia state, and Vue Router patterns for Vue projects. Trigger when building or reviewing a Vue application. Do NOT use for React or Svelte projects.
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
  tags: [vue, composition-api, pinia]
---

# Purpose
Provides Vue 3 Composition API, Pinia store, and Vue Router patterns for building well-structured Vue applications.

# When to use this skill
Use when:
- Building or reviewing a Vue 3 application
- Migrating a Vue 2 Options API app to Vue 3 Composition API

Do NOT use when:
- Working in React (use react-typescript) or Svelte (use svelte)
- Using Vue 2 without intending to migrate

# Operating procedure
1. Use the Composition API with `<script setup>` for all new components
2. Define state with `ref` and `reactive`; use `computed` for derived state
3. Manage global state with Pinia stores; avoid Vuex in new projects
4. Use Vue Router with typed routes for navigation
5. Apply TypeScript generics to composables for type-safe reuse

# Output defaults
Vue 3 components using `<script setup>` with Composition API, Pinia stores, and TypeScript types.

# Failure handling
If reactivity breaks unexpectedly, check that reactive objects are not being destructured (which breaks reactivity). Use `toRefs()` for safe destructuring.
