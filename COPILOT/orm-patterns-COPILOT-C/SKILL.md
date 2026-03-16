---
name: orm-patterns
description: Sets expectations for ORM model design, query boundaries, migration use, and avoiding ORM misuse. Use when working with SQLAlchemy, GORM, or similar. Do NOT use for raw SQL optimisation.
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
  tags: [orm, sqlalchemy, gorm, migrations, models]
---

# Purpose
Guides ORM model definition, relationship loading, transaction boundaries, and migration management.

# When to use this skill
Use when:
- Defining ORM models and relationships
- Deciding between lazy and eager loading
- Writing migration scripts with Alembic or goose

Do NOT use when:
- Writing raw analytical SQL (use postgresql or bigquery)
- Schema design from scratch (use data-model)

# Operating procedure
1. Keep ORM models thin; put business logic in service layer
2. Declare relationships explicitly with lazy/eager load choice documented
3. Use session.add() + commit() in a single transaction per unit of work
4. Never expose ORM objects directly in API responses; map to DTOs
5. Run migrations in CI; never auto-migrate in production startup
6. Test relationships with factory fixtures, not raw SQL inserts

# Output defaults
Model definitions + migration file + loading strategy notes.

# Failure handling
On ORM deadlock, retry with exponential backoff. On migration failure, roll back and investigate before re-running.
