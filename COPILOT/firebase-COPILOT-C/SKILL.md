---
name: firebase
description: Covers Firebase architecture choices, Firestore data modeling, security rules, client/server usage, and deployment caveats. Use when building or debugging Firebase-backed applications.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: cloud-platform-devops
  priority: P1
  maturity: draft
  risk: low
  tags: [firebase, firestore, authentication, google]
---

# Purpose
Covers Firebase architecture choices, Firestore data modeling, security rules, client/server usage, and deployment caveats.

# When to use this skill
Use when:
- Building apps with Firebase Auth, Firestore, or Realtime Database
- Writing Firebase security rules
- Deploying Firebase Functions or Hosting

Do NOT use when:
- GCP services without Firebase SDK involvement
- Projects using SQL databases instead of Firestore

# Operating procedure
1. Design Firestore data model for query patterns
2. Write security rules with least-privilege access
3. Configure Firebase Auth providers
4. Deploy via firebase deploy with .firebaserc
5. Test rules with Firebase emulator suite

# Output defaults
Firestore schemas, security rules, firebase.json configs, auth configuration docs

# Failure handling
If security rules block valid requests, use emulator to trace rule evaluation.
