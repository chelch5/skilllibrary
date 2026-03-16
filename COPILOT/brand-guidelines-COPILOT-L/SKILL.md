---
name: brand-guidelines
description: Translates brand rules (tone, colour, typography, imagery, consistency) into actionable design and copy decisions. Trigger when producing or reviewing content that must conform to a brand identity. Do NOT use for generic frontend design without brand constraints (use frontend-design).
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P2
  maturity: stable
  risk: low
  tags: [brand, design, tone, typography, colour, consistency]
---

# Purpose
Applies brand identity rules to ensure design and copy outputs are consistent, on-brand, and production-ready.

# When to use this skill
Use when:
- Creating marketing copy, UI text, or visual assets that must match a brand
- Reviewing content for brand consistency before publication
- Establishing brand tokens for a new product or feature

Do NOT use when:
- No brand guidelines exist or have been provided (fall back to `frontend-design`)
- The task is purely functional UI with no brand expression

# Operating procedure
1. Load brand guidelines: colour palette, typography scale, tone-of-voice rules, logo usage
2. Identify all touchpoints in scope: copy, colour, type, spacing, imagery
3. For copy: apply tone rules (formal/casual, active/passive, vocabulary restrictions)
4. For colour: verify usage against palette roles (primary, secondary, error, neutral)
5. For typography: verify heading/body/caption hierarchy matches the type scale
6. Flag any off-brand choices with the specific rule violated and a corrected alternative
7. Produce a compliance summary: pass / fix-needed per touchpoint

# Output defaults
Annotated content or design spec with pass/fail per brand rule, plus corrected alternatives for failures.

# Failure handling
If brand guidelines are incomplete, state which areas lack guidance and apply reasonable defaults. Do not invent brand rules.
