---
name: decision-packet-builder
description: "Batches unresolved major choices with options, consequences, and recommendations instead of drip-feeding questions. This matches your own preference for grouped decision handling. Trigger when the task context clearly involves decision packet builder."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: planning-review-and-critique
  priority: P1
  maturity: draft
  risk: low
  tags: [decisions, tradeoffs, batch]
---

# Purpose
Collects all pending major decisions into a single structured packet so they can be reviewed, debated, and resolved in one pass rather than as a stream of interruptions. This follows the Architecture Decision Record (ADR) pattern: each decision is documented with context, options, consequences, and a recommendation, creating a durable record of why choices were made.

# When to use this skill
Use when:
- The user says "what decisions do we need to make?", "build a decision packet", "batch the open questions", or "prepare decisions for review"
- A project is stalled because multiple unresolved choices are blocking each other
- A stakeholder review is upcoming and decisions need to be prepared with context
- Planning is producing more questions than answers and they need organization
- Multiple people need to align on choices before work proceeds

Do NOT use when:
- Only one decision needs to be made (just make a recommendation directly)
- The decisions are already resolved and need implementation
- The user wants tradeoff analysis for a single option comparison (use `tradeoff-analysis`)
- The user wants risks identified (use `premortem`)

# Operating procedure
1. **Identify all open decisions**: Scan the plan, conversation, or document for:
   - Explicit questions ("Should we use X or Y?")
   - "TBD" markers
   - Forks in the approach
   - Options mentioned but not chosen
   - Unstated choices that must be made before implementation

2. **Filter for major decisions**: Only include decisions that:
   - Block other work if unresolved
   - Are hard to reverse once made
   - Have meaningful tradeoffs between options
   - Require stakeholder input or alignment

3. **Group by dependency**: Identify which decisions block others. Order them: decisions that must be made first appear first.

4. **For each decision, write a structured ADR-style entry**:
   - **Decision ID**: Short label (D1, D2, etc.)
   - **Question**: One clear sentence stating what must be decided
   - **Context**: Why this matters, what happens downstream, what triggered this decision point
   - **Options**: 2-4 concrete options, each with a one-sentence description
   - **Tradeoffs**: For each option, the key upside and downside (one sentence each)
   - **Recommendation**: The option you recommend and why, stated directly—do not hedge
   - **Reversibility**: Easy / Moderate / Hard to change later
   - **Deadline**: When this must be decided to avoid blocking progress

5. **Summarize the decision graph**: Show which decisions depend on which, using notation like "D2 depends on D1".

6. **Flag irreversible decisions**: Mark any choice that would be very costly to undo with ⚠️ HIGH STAKES.

# Output defaults
A structured **Decision Packet** document with:
- Header: project name, date, author
- One entry per decision using the template above
- A **Decision Dependencies** section showing the order
- A **Immediate Attention Required** section for decisions blocking 2+ others

Example format per decision:
```
## D1: Database selection

**Question**: Which database should we use for user data storage?

**Context**: This choice affects data model design, query patterns, and operational complexity. Must be decided before schema design begins.

**Options**:
1. PostgreSQL — Mature, relational, strong consistency
2. MongoDB — Document store, flexible schema, eventual consistency
3. DynamoDB — Managed, serverless, pay-per-request

**Tradeoffs**:
| Option     | Upside                           | Downside                        |
|------------|----------------------------------|---------------------------------|
| PostgreSQL | Team expertise, ACID guarantees  | Self-managed, scaling overhead  |
| MongoDB    | Schema flexibility               | Less team experience            |
| DynamoDB   | Zero ops, auto-scaling           | Vendor lock-in, query limits    |

**Recommendation**: PostgreSQL. Team has 5+ years of experience, and the use case fits relational patterns. Scaling concerns are premature optimization.

**Reversibility**: Hard — data migration required
**Deadline**: Before sprint 2 planning (March 10)
```

# References
- https://github.com/joelparkerhenderson/architecture-decision-record — ADR templates and examples
- Nygard, M. "Documenting Architecture Decisions" — original lightweight ADR format
- https://adr.github.io/ — ADR tooling and community standards

# Failure handling
If insufficient context exists to produce Options or Tradeoffs for a decision:
1. Mark that decision as **Needs More Context**
2. List specifically what information is required
3. Include the decision in the packet but flag it as incomplete
4. Proceed with other decisions that can be fully analyzed
