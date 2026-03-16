---
name: analytics-instrumentation
description: Defines events, funnels, naming conventions, and capture rules so product analytics are useful rather than noisy. Trigger when implementing or auditing analytics in a web app. Do NOT use for backend performance monitoring.
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
  tags: [analytics, instrumentation, events]
---

# Purpose
Designs a clean analytics event taxonomy and instrumentation plan so product analytics yield actionable insights without noise.

# When to use this skill
Use when:
- Implementing analytics tracking for a new or existing web product
- Auditing an analytics implementation for naming consistency and coverage gaps

Do NOT use when:
- Setting up backend performance monitoring or application metrics
- Implementing error tracking (use a dedicated error monitoring tool)

# Operating procedure
1. Define the analytics taxonomy: object-action naming (user_clicked_button, page_viewed)
2. Identify key user funnels and ensure each step has a corresponding event
3. Define required properties for each event type (user_id, session_id, timestamp)
4. Implement a typed event dispatch helper to enforce schema at call sites
5. Validate that events appear correctly in the analytics platform before shipping

# Output defaults
An analytics event schema document with event names, required properties, and funnel mapping.

# Failure handling
If an event fires with missing required properties, log a warning and optionally block the event to prevent data quality degradation.
