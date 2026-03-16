---
name: spec-pack-normalizer
description: "Normalizes scattered notes, chats, specs, and requirements into one canonical brief and decision packet. You repeatedly work from messy source material, so this skill is foundational. Trigger when the task context clearly involves spec pack normalizer."
source: github.com/scafforge/session
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: package-scaffolding
  priority: P0
  maturity: draft
  risk: low
  tags: [spec, normalization, brief]
---

# Purpose
Transforms messy, multi-source project inputs—chat transcripts, meeting notes, scattered docs, pasted requirements—into a single canonical brief with explicit decisions and constraints. The output becomes the authoritative source of truth that all downstream scaffolding and implementation skills reference.

# When to use this skill
Use when:
- Starting a project with inputs spread across multiple formats (Slack threads, Google Docs, email, voice transcripts)
- Requirements exist but contradict each other or have unstated assumptions
- Inherited a project with documentation but no clear "what are we actually building" summary
- Need to reconcile stakeholder input before committing to implementation

Do NOT use when:
- A clean, single-source spec already exists in standard format
- Working on implementation tasks where requirements are already clear
- Doing post-hoc documentation of a completed project

# Operating procedure
1. **Inventory inputs**: List all source materials with file paths or URLs. Note format type (chat, doc, recording transcript, diagram).

2. **Extract claims**: Read each source and extract factual claims about:
   - Problem being solved
   - Target users
   - Required capabilities (must-have)
   - Desired capabilities (nice-to-have)
   - Explicit constraints (budget, timeline, tech restrictions)
   - Implicit assumptions

3. **Detect conflicts**: Compare claims across sources. Flag where Source A says X but Source B implies Y. Examples:
   - "Mobile-first" vs. design mocks showing desktop-only
   - "Launch in 2 weeks" vs. feature list requiring 2 months
   - "Simple MVP" vs. enterprise compliance requirements

4. **Resolve or escalate**: For each conflict:
   - If one source is clearly authoritative (e.g., signed-off PRD > casual chat), resolve in its favor
   - If unclear, add to DECISIONS.md as open question with options and recommendation

5. **Produce BRIEF.md**:
   ```markdown
   # Project Brief: [Name]
   
   ## Problem Statement
   [2-3 sentences: what problem, for whom, why now]
   
   ## Success Criteria
   - [Measurable outcome 1]
   - [Measurable outcome 2]
   
   ## Scope
   ### In Scope
   - [Capability 1]
   - [Capability 2]
   
   ### Out of Scope
   - [Explicitly excluded item 1]
   
   ## Key Decisions
   - [Decision 1]: [Choice made] — rationale: [why]
   
   ## Open Questions
   - [Question needing stakeholder input]
   ```

6. **Produce CONSTRAINTS.md**:
   ```markdown
   # Constraints
   
   ## Hard Constraints (non-negotiable)
   - Timeline: [date or "none specified"]
   - Budget: [amount or "none specified"]
   - Tech stack: [requirements or "flexible"]
   - Compliance: [requirements or "none"]
   
   ## Soft Constraints (preferences)
   - [Preference with flexibility noted]
   ```

7. **Produce DECISIONS.md**:
   ```markdown
   # Decision Log
   
   ## Resolved
   | ID | Question | Decision | Rationale | Date |
   |----|----------|----------|-----------|------|
   | D001 | [question] | [answer] | [why] | [date] |
   
   ## Open
   | ID | Question | Options | Recommendation | Blocker For |
   |----|----------|---------|----------------|-------------|
   | D002 | [question] | A, B, C | A because... | ticket-pack |
   ```

8. **Link sources**: At the bottom of BRIEF.md, add `## Sources` section listing every input document used, enabling traceability.

# Output defaults
Three files in `docs/`:
- `BRIEF.md` — canonical project summary (500-1500 words)
- `CONSTRAINTS.md` — hard and soft boundaries
- `DECISIONS.md` — resolved and open decision log

# References
- Shape Up "Write the Pitch" (problem, appetite, solution, rabbit holes, no-gos): https://basecamp.com/shapeup

# Failure handling
- **Insufficient input**: If sources don't contain minimum viable information (problem + users + at least one capability), stop and request: "Need at minimum: what problem, for whom, one concrete feature"
- **All conflicts, no resolution**: If >50% of claims conflict with no clear authority, produce BRIEF.md with `status: DRAFT-UNRESOLVED` header and list all conflicts in DECISIONS.md as open questions
- **Scope creep detected**: If nice-to-haves exceed must-haves by 2:1, flag in CONSTRAINTS.md and recommend scope cut before proceeding
