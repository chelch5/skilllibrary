---
name: firebase-rules
description: Handles Firebase security rules design, access control, and rule testing. Use when writing or reviewing Firestore/Storage security rules. Do NOT use for Firebase SDK client usage.
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
  tags: [firebase, security-rules, firestore, access-control]
---

# Purpose
Produces correct, least-privilege Firebase security rules with tests that verify both allow and deny paths.

# When to use this skill
Use when:
- Writing Firestore or Storage security rules
- Reviewing rules for over-permissive patterns
- Adding role-based access to Firebase collections

Do NOT use when:
- Using Firebase client SDK patterns (use firebase-sdk)
- Designing the data model itself (use data-model)

# Operating procedure
1. Map user roles to document ownership and access levels
2. Write rules starting from deny-all default
3. Add explicit allow conditions with minimal scope
4. Test each rule with @firebase/rules-unit-testing
5. Cover both positive (allow) and negative (deny) test cases
6. Review for wildcard paths that may expose unintended data

# Output defaults
Rules file + unit test suite covering allow and deny cases.

# Failure handling
If a rule change causes a regression test to fail, revert and re-scope. Never deploy rules without running the test suite.
