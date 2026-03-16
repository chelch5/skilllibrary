---
name: image-editor
description: Handles focused image editing, transformation, cropping, resizing, or export tasks as a reusable skill pattern. Use for programmatic image processing tasks.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: docs-artifacts-media
  priority: P2
  maturity: draft
  risk: low
  tags: [image, editing, transform, media]
---

# Purpose
Handles focused image editing, transformation, cropping, resizing, or export tasks as a reusable skill pattern.

# When to use this skill
Use when:
- Resizing, cropping, or converting image formats programmatically
- Applying filters or transformations to images
- Batch processing images for consistent output

Do NOT use when:
- Generative AI image creation (use image-prompt-direction)
- Advanced photo retouching or manual editing

# Operating procedure
1. Identify required transformation (resize, crop, convert, filter)
2. Use appropriate library (Pillow, sharp, imagemagick)
3. Apply transformation preserving original if needed
4. Validate output dimensions and file size
5. Export to target format with quality settings

# Output defaults
Processed image files at target dimensions and format

# Failure handling
If image quality degrades, increase quality settings or check source resolution.
