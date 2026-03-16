---
name: flask
description: Applies Flask app structure, extension boundaries, and request handling patterns. Use when building a Python web service with Flask. Do NOT use when FastAPI is preferred for async workloads.
source: created
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: backend-api-and-data
  priority: P2
  maturity: draft
  risk: low
  tags: [flask, python, web, blueprints, wsgi]
---

# Purpose
Establishes Flask application factory pattern, blueprint organisation, and safe request handling conventions.

# When to use this skill
Use when:
- Scaffolding a new Flask service with blueprints
- Adding Flask extensions (SQLAlchemy, Migrate, Login)
- Reviewing request context usage and teardown

Do NOT use when:
- Async I/O is central (use FastAPI)
- Front-end templating is the primary concern

# Operating procedure
1. Use application factory pattern (create_app())
2. Organise routes into blueprints by domain
3. Register extensions on the app instance, not at module level
4. Use g and request proxies only inside request context
5. Add error handlers for 400, 404, 500
6. Run with gunicorn in production, not flask run

# Output defaults
App factory skeleton + blueprint template + extension registration pattern.

# Failure handling
If an extension is used outside of application context, wrap in app.app_context(). Log and return JSON error responses; avoid HTML error pages for APIs.
