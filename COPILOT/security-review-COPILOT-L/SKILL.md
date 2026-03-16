---
name: security-review
description: Reviews trust boundaries, secrets handling, input validation, and attack surfaces in a read-only lane. Use when a feature touches auth, secrets, user input, or external integrations. Do NOT use for general code quality review (use `code-review`).
source: github.com/gpttalker/agent-skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: agent-role-candidates
  priority: P1
  maturity: draft
  risk: low
  tags: [security, audit, trust-boundaries, secrets, validation]
---

# Purpose
Performs a read-only security review focusing on trust boundaries, secrets handling, input validation, and exploitable attack surfaces.

# When to use this skill
Use when:
- A feature touches authentication, authorisation, or session management
- User input is processed or passed to external systems
- Secrets, tokens, or credentials are involved
- External API integrations are added or changed

Do NOT use when:
- The review is for general code quality (use `code-review`)
- The feature has no external surface or privileged operations

# Operating procedure
1. Map trust boundaries: what enters from outside, what leaves to outside
2. Check secrets handling: env vars, no hardcoding, rotation policy
3. Check input validation: sanitisation, length limits, type checks
4. Check auth: correct enforcement on every protected route/operation
5. Identify injection risks: SQL, command, template, SSRF
6. Report findings by severity: critical → high → medium → low

# Output defaults
Severity-ranked finding list. Each finding: location, vulnerability class, impact, recommended fix. Read-only — no code changes.

# Failure handling
If access to secrets config is unavailable, note the gap and flag for manual review.
