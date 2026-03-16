---
name: canvas-design
description: Designs visual layouts inside canvas-based surfaces (HTML Canvas, SVG, Fabric.js, Konva, p5.js) with attention to composition, hierarchy, and interactivity. Trigger when building canvas-rendered UIs, data visualisations, or interactive graphics. Do NOT use for DOM-based UI layout (use frontend-design or tailwind-shadcn).
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
  tags: [canvas, svg, graphics, visualisation, composition]
---

# Purpose
Produces well-composed canvas and SVG-based visuals: data visualisations, interactive graphics, and custom rendered UI surfaces.

# When to use this skill
Use when:
- Building charts, diagrams, or data visualisations with Canvas or SVG
- Implementing interactive graphics with drag, zoom, or pan
- Designing a custom rendered UI surface (game HUD, canvas editor, whiteboard)

Do NOT use when:
- The UI is standard DOM components (use `frontend-design`)
- The task is static image generation without interactivity

# Operating procedure
1. Define the canvas coordinate space: width, height, pixel ratio (handle HiDPI)
2. Establish a scene graph or render loop structure appropriate to the framework
3. Apply visual hierarchy: primary elements large/high-contrast, secondary elements subordinate
4. Implement interactivity (if needed): hit-testing, event delegation, cursor feedback
5. Optimise render performance: dirty-flag redraws, layer separation for static/dynamic content
6. Test at multiple viewport sizes and pixel densities

# Output defaults
Canvas/SVG implementation with documented coordinate system, render loop, and interaction handlers.

# Failure handling
On render performance issues, profile with requestAnimationFrame timing and isolate expensive draw calls. On HiDPI blurriness, ensure devicePixelRatio scaling is applied to both canvas size and context transform.
