---
name: testing-web
description: Applies unit, component, integration, and browser-level testing strategies to frontend projects. Trigger when setting up or expanding a frontend test suite. Do NOT use for backend or API testing.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: web-frontend-and-design
  priority: P1
  maturity: draft
  risk: low
  tags: [testing, frontend, vitest]
---

# Purpose
Provides a layered frontend testing strategy covering unit tests, component tests, integration tests, and browser-level end-to-end tests.

# When to use this skill
Use when:
- Setting up a frontend test suite from scratch
- Expanding test coverage in an existing web application

Do NOT use when:
- Testing backend APIs or server-side logic
- General test strategy for non-web projects

# Operating procedure
1. Set up Vitest (or Jest) for unit and component tests
2. Use Testing Library for component tests that test behavior not implementation
3. Write integration tests for key user flows using Testing Library with a real DOM
4. Add Playwright or Cypress for critical end-to-end browser tests
5. Aim for high coverage on business logic; avoid testing implementation details

# Output defaults
A test suite with unit, component, integration, and E2E tests plus a CI configuration.

# Failure handling
If a test fails flakily in CI, quarantine it and investigate the root cause before re-enabling. Do not accept flaky tests in the main test suite.
