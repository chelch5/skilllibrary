---
name: cargo-lock-manager
description: A Rust dependency management skill focused on Cargo.lock handling, dependency updates, and supply-chain discipline. Use for Rust project dependency workflows.
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
  tags: [rust, cargo, dependencies, lockfile]
---

# Purpose
A Rust dependency management skill focused on Cargo.

# When to use this skill
Use when:
- Managing Cargo.toml dependencies and Cargo.lock updates
- Auditing Rust dependencies for security issues
- Resolving version conflicts in Cargo dependency graph

Do NOT use when:
- Non-Rust projects
- General package management outside the Cargo ecosystem

# Operating procedure
1. Review current dependency tree with cargo tree
2. Update dependencies with cargo update selectively
3. Run cargo audit for security vulnerabilities
4. Resolve version conflicts by pinning or upgrading
5. Commit Cargo.lock changes with justification

# Output defaults
Updated Cargo.toml and Cargo.lock, audit report, conflict resolution notes

# Failure handling
If cargo audit finds RUSTSEC vulnerabilities, patch or document accepted risk immediately.
