---
name: firebase-sdk
description: Applies client/server Firebase SDK usage conventions and integration cautions. Use when integrating Firebase into a web or server app. Do NOT use for security rules authoring.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: backend-api-and-data
  priority: P2
  maturity: draft
  risk: low
  tags: [firebase, sdk, firestore, auth, realtime-db]
---

# Purpose
Guides correct Firebase SDK initialisation, auth flow, Firestore query patterns, and offline behaviour.

# When to use this skill
Use when:
- Initialising Firebase in a new web or Node.js project
- Writing Firestore read/write operations with correct error handling
- Handling auth state changes and token refresh

Do NOT use when:
- Writing Firestore security rules (use firebase-rules)
- BigQuery or server-side analytics (use bigquery)

# Operating procedure
1. Initialise Firebase once at app entry point; guard against double init
2. Use modular SDK (v9+) for tree-shaking
3. Wrap Firestore operations in try/catch; handle permission-denied explicitly
4. Use onAuthStateChanged listener; never store tokens in localStorage
5. Enable offline persistence only where explicitly needed
6. Test with Firebase Emulator Suite before production

# Output defaults
Initialisation snippet + Firestore CRUD examples + auth flow skeleton.

# Failure handling
On permission-denied, surface a clear user error. On network errors, retry with exponential backoff. Never cache stale auth state.
