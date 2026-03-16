---
name: seo-structured-data
description: Adds search-oriented metadata, sitemaps, JSON-LD schema, and crawl-aware content structure to web projects. Trigger when building a public web product that needs search visibility. Do NOT use for internal tools or auth-gated apps.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P2
  maturity: draft
  risk: low
  tags: [seo, structured-data, metadata]
---

# Purpose
Implements SEO best practices including meta tags, JSON-LD structured data, sitemaps, and crawlability improvements for public web applications.

# When to use this skill
Use when:
- Building a public-facing web app that needs to rank in search engines
- Auditing an existing web app's SEO health

Do NOT use when:
- The app is internal or auth-gated and not crawlable
- The product does not benefit from organic search traffic

# Operating procedure
1. Add title, description, and Open Graph meta tags to all pages
2. Implement JSON-LD structured data for relevant content types (article, product, FAQ)
3. Generate a sitemap.xml with correct priorities and change frequencies
4. Ensure all important content is accessible without JavaScript
5. Validate structured data with Google's Rich Results Test

# Output defaults
A set of meta tags, JSON-LD schema snippets, and sitemap configuration for the web app.

# Failure handling
If structured data validation fails, fix the specific violations reported by the validator. Do not guess at the correct schema format.
