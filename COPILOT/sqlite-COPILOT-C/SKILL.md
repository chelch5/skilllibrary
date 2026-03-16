---
name: sqlite
description: Defines file-backed persistence, migration, concurrency, and testing patterns for SQLite. Use for lightweight local or embedded databases. Do NOT use for multi-writer server deployments.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: backend-api-and-data
  priority: P1
  maturity: draft
  risk: low
  tags: [sqlite, embedded, local, migrations, concurrency]
---

# Purpose
Establishes safe SQLite usage for single-writer embedded databases with proper WAL mode, migrations, and test isolation.

# When to use this skill
Use when:
- Building a CLI tool, desktop app, or agent that needs local persistence
- Embedding a database without a server process
- Designing schema migrations for a file-backed DB

Do NOT use when:
- Multiple writers or high concurrency are required (use postgresql)
- Analytics at scale (use bigquery)

# Operating procedure
1. Enable WAL mode (PRAGMA journal_mode=WAL) on open
2. Set PRAGMA busy_timeout to handle concurrent reads
3. Run migrations at startup via versioned SQL files
4. Use parameterised queries exclusively; never interpolate values
5. For tests, use :memory: databases per test case
6. Back up with .backup() API before destructive operations

# Output defaults
Database initialisation snippet + migration runner + test fixture helper.

# Failure handling
On SQLITE_BUSY, retry with exponential backoff. On corruption, restore from backup and log the incident.
