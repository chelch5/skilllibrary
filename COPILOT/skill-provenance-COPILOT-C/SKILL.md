---
name: skill-provenance
description: "Records where a skill came from, what evidence informed it, and what assumptions it encodes. Helps avoid mysterious prompt blobs. Trigger when the task context clearly involves skill provenance."
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: meta-skill-engineering
  priority: P1
  maturity: draft
  risk: low
  tags: [provenance, traceability, evidence]
---

# Purpose
Documents a skill's origin, the evidence or reasoning that informed each design decision, and the assumptions it encodes — so future maintainers know why the skill works the way it does and what would need to change if context changes.

# When to use this skill
Use when:
- The user says "document the provenance of this skill", "where did this skill come from?", or "what assumptions does this skill make?"
- A skill was created without documentation and its reasoning is opaque
- A skill is being promoted from draft to stable and requires documented evidence of its design basis
- An audit of a skill library needs traceable origins for compliance or quality purposes

Do NOT use when:
- The skill is brand new and provenance documentation can be written inline during authoring
- The goal is to evaluate the skill's quality (use `skill-evaluation`)
- The goal is to track changes over time rather than document origins (use git history instead)

# Operating procedure
1. **Identify the origin category**: Was this skill:
   - **Created from scratch** (author reasoning from first principles)
   - **Adapted from a source** (based on an existing pattern, framework, or document — name it)
   - **Derived from observations** (built from watching real usage patterns — describe the pattern)
   - **Ported from another library** (name the source repo and original author)
2. **Document the design decisions**: For each major structural choice in the skill (why this number of steps, why these specific trigger phrases, why this output format), write one sentence explaining the reasoning
3. **List the evidence base**: What data, usage observations, user feedback, or cited sources informed the skill? If none exists, state "No evidence base — authored from first principles"
4. **Name the assumptions explicitly**: What does the skill assume about the user, the context, the tooling, or the agent that is not stated in the operating procedure?
5. **Record the validation history**: Has the skill been tested? How? Against what prompts? What were the results? If not tested, state that
6. **Write a `PROVENANCE.md`** in the skill folder with the above sections: Origin, Design Decisions, Evidence Base, Assumptions, Validation History
7. **Update the frontmatter `source` field** if the origin is a specific document, repo, or author

# Output defaults
A `PROVENANCE.md` file in the skill folder with sections: Origin, Design Decisions, Evidence Base, Assumptions, and Validation History.

# Failure handling
If the skill's original author or design reasoning cannot be recovered, document it as **Unknown** for those sections rather than guessing. State the date the provenance was reconstructed and by whom.
