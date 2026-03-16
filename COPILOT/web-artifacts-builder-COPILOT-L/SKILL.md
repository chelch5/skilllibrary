---
name: web-artifacts-builder
description: Produces polished web-rendered artefacts — interactive HTML reports, static site pages, data dashboards, and structured web content — using Claude's artefact rendering capability. Trigger when the user wants a visual, shareable, or interactive web output rather than plain text. Do NOT use for standard prose or code-only responses.
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
  tags: [artifacts, html, dashboard, interactive, visualisation, web]
---

# Purpose
Builds visually polished, self-contained web artefacts (HTML/CSS/JS) that render directly in the canvas: dashboards, reports, landing pages, data visualisations, and interactive tools.

# When to use this skill
Use when:
- The user asks for a "dashboard", "report", "visualisation", or "interactive" output
- A chart, table, or structured data set would benefit from visual presentation
- A shareable, embeddable HTML page is more useful than a markdown response

Do NOT use when:
- Plain text or markdown is sufficient
- The user needs a full application with backend state (not a self-contained artefact)

# Operating procedure
1. Determine the artefact type: dashboard, report, landing page, tool, or visualisation
2. Choose the right rendering approach: Chart.js for charts, vanilla JS tables for data, CSS Grid for layout
3. Keep everything self-contained: inline CSS and JS, no external CDN calls that might fail
4. Apply visual polish: consistent colour palette, clear typography, appropriate whitespace
5. For data: validate the data shape before rendering, handle empty/null gracefully
6. Add interactivity where it adds genuine value (filter, sort, drill-down) — not for decoration

# Output defaults
A single self-contained HTML artefact ready to render in the canvas. Minify only if size is an issue. Always include a visible title and data source attribution.

# Failure handling
If data is malformed, render a clear "No data available" state rather than a broken chart. If a requested library would require an external CDN, implement the feature in vanilla JS instead.
