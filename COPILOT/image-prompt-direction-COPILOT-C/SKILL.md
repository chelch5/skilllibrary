---
name: image-prompt-direction
description: Crafts effective prompts for AI image generation tools (Midjourney, DALL-E, Stable Diffusion) and provides creative direction for visual outputs. Use when guiding AI image creation.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: business-research-and-optional-domains
  priority: P2
  maturity: draft
  risk: low
  tags: [image-generation, prompts, ai-art, creative-direction]
---

# Purpose
Crafts effective prompts for AI image generation tools (Midjourney, DALL-E, Stable Diffusion) and provides creative direction for visual outputs.

# When to use this skill
Use when:
- Writing effective prompts for AI image generation
- Providing creative direction for visual content
- Iterating on generated images to match a vision

Do NOT use when:
- Programmatic image processing (use image-editor)
- Algorithmic art generation (use algorithmic-art)

# Operating procedure
1. Define visual goal with style, subject, mood references
2. Structure prompt with subject, context, style, quality modifiers
3. Iterate with negative prompts to remove unwanted elements
4. Test across multiple seeds for variation
5. Document successful prompt patterns for reuse

# Output defaults
Image generation prompts with style references, iteration notes, and successful seed values

# Failure handling
If outputs don't match intent, add explicit negative prompts. Avoid ambiguous descriptors.
