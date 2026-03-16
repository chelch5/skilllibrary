---
name: algorithmic-art
description: Explores computational and generative art creation workflows, from procedural generation to creative coding. Use when creating art through algorithms rather than manual drawing.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: game-engines-and-creative-tech
  priority: P2
  maturity: draft
  risk: low
  tags: [generative-art, creative-coding, algorithmic, visual]
---

# Purpose
Explores computational and generative art creation workflows, from procedural generation to creative coding.

# When to use this skill
Use when:
- Generating visual art through code (fractals, noise, L-systems)
- Building procedural texture or pattern generators
- Creative coding projects with p5.js, Processing, or shaders

Do NOT use when:
- Manual digital illustration or photo editing
- AI image generation prompting (use image-prompt-direction instead)

# Operating procedure
1. Define generative parameters and seed control
2. Implement core algorithm (noise, recursion, L-system)
3. Add interactive controls for parameter exploration
4. Export outputs at target resolution
5. Document algorithm and interesting seed values

# Output defaults
Generative code sketches, exported images/animations, parameter documentation

# Failure handling
If output looks wrong, isolate parameter ranges. Add visual debug overlays.
