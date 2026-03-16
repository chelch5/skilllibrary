---
name: data-model
description: Designs entities, relationships, invariants, and migration-sensitive structure in the data layer. Use when planning or evolving a schema. Do NOT use for runtime query optimisation.
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
  tags: [data-model, schema, erd, migrations, entities]
---

# Purpose
Produces a well-reasoned data model with clear entity boundaries, invariants documented, and a safe migration path.

# When to use this skill
Use when:
- Designing a new schema from requirements
- Evaluating an existing schema for structural problems
- Planning a migration that must not break production

Do NOT use when:
- Optimising existing queries (use postgresql or bigquery)
- API surface design (use api-contracts)

# Operating procedure
1. List entities and their core attributes
2. Define relationships: one-to-many, many-to-many, optional vs required
3. Identify invariants and where they are enforced (DB vs app layer)
4. Plan migrations: additive first, destructive last
5. Document nullability decisions explicitly
6. Review for normalisation vs intentional denormalisation

# Output defaults
Entity list with relationship diagram (Mermaid or prose) + migration plan.

# Failure handling
If invariants cannot be enforced at the DB level, document the app-layer guard required. Never proceed with a destructive migration without a tested rollback script.
