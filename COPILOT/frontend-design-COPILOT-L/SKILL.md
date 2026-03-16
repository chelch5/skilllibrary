---
name: frontend-design
description: Applies design judgement to frontend work — layout, visual hierarchy, spacing, colour, typography, and interaction polish. Trigger when a UI needs aesthetic improvement or design critique beyond functional correctness. Do NOT use for backend logic or for purely structural HTML without design intent.
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
  tags: [design, layout, typography, colour, hierarchy, polish]
---

# Purpose
Elevates frontend UIs from functional to polished by applying design principles: visual hierarchy, consistent spacing, readable typography, and intentional colour.

# When to use this skill
Use when:
- A UI is functional but looks unpolished or inconsistent
- A design review is needed before shipping a user-facing feature
- Implementing a Figma or design spec with pixel-level fidelity

Do NOT use when:
- The task is purely structural/semantic HTML with no visual design intent
- Backend or API work is in scope

# Operating procedure
1. Audit visual hierarchy: is the most important element visually dominant?
2. Check spacing consistency: does the layout use a coherent spacing scale (4px/8px grid)?
3. Review typography: heading/body/caption roles clear? Line-height and measure comfortable?
4. Check colour: sufficient contrast (WCAG AA minimum), intentional not arbitrary palette use
5. Review interactive states: hover, focus, active, disabled — are they all handled?
6. Check responsive behaviour at mobile (375px), tablet (768px), and desktop (1280px)
7. Identify and fix the three highest-impact visual problems

# Output defaults
Annotated list of design issues with severity and specific fix (CSS property, token name, or component change). Revised code where feasible.

# Failure handling
If a design system or token set exists, reference it for fixes. If no design spec exists, apply reasonable defaults and document assumptions.
