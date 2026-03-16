---
name: webapp-testing
description: End-to-end webapp testing strategy covering playwright E2E tests, component testing, API mocking, and the reconnaissance-then-action pattern. Trigger when writing or reviewing tests for a web application. Do NOT use for unit-only testing of pure functions (use the testing skill).
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
  tags: [testing, playwright, e2e, component-testing, web]
---

# Purpose
Establishes a complete webapp testing strategy: reconnaissance of the app structure, E2E tests for critical paths, component tests for UI logic, and API mocking to isolate the frontend.

# When to use this skill
Use when:
- Writing Playwright or Cypress E2E tests for a web application
- Setting up a component testing layer with Vitest/Testing Library
- Diagnosing flaky tests or poor coverage in a webapp test suite

Do NOT use when:
- Testing pure backend logic or utilities (use `testing`)
- The app has no UI (use API-focused testing approaches)

# Operating procedure

**Reconnaissance phase (before writing tests)**
1. Map the application's critical user journeys (auth, primary value action, error states)
2. Identify shared fixtures: test users, seed data, auth tokens
3. Check what's already tested — avoid duplicating existing coverage

**Implementation phase**
1. Write E2E tests for the top 3 critical journeys using Playwright's `page.goto` + role-based locators (`getByRole`, `getByLabel`) — never CSS selectors
2. Mock external APIs at the network layer (`page.route`) to eliminate flakiness
3. Write component tests for stateful UI logic using Testing Library's `userEvent`
4. Use `expect.poll` for async state — never `waitForTimeout`
5. Run tests in CI with `--reporter=html` to capture failure screenshots

**Review phase**
1. Check: do tests verify behaviour, not implementation details?
2. Check: are locators resilient to CSS/class changes?
3. Check: does every test clean up its state?

# Output defaults
Playwright test files organised by journey, with page object models for reusable interactions and a `playwright.config.ts` with sensible defaults.

# Failure handling
On flaky test: add `--retries=2` temporarily, identify the non-deterministic element, fix the root cause (network mock, await condition), remove retries. Never leave retries as a permanent fix.
