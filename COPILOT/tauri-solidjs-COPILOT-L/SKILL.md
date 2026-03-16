---
name: tauri-solidjs
description: A desktop app stack skill combining Tauri (Rust backend) and SolidJS (frontend) conventions. Use when building cross-platform desktop apps with this stack.
source: github.com/anthropics/skills
license: Apache-2.0
compatibility:
  clients: [openai-codex, gemini-cli, opencode, github-copilot]
metadata:
  owner: skill-library
  category: external-reference-seeds
  priority: P2
  maturity: draft
  risk: low
  tags: [tauri, solidjs, desktop, rust]
---

# Purpose
A desktop app stack skill combining Tauri (Rust backend) and SolidJS (frontend) conventions.

# When to use this skill
Use when:
- Building desktop applications with Tauri and SolidJS
- Implementing Tauri commands and IPC between Rust and SolidJS
- Configuring Tauri app settings and platform-specific behavior

Do NOT use when:
- Pure web apps without Tauri wrapper
- Electron-based desktop apps

# Operating procedure
1. Set up Tauri project with SolidJS frontend
2. Define Tauri commands in Rust with #[tauri::command]
3. Invoke commands from SolidJS via invoke()
4. Configure tauri.conf.json for permissions and window settings
5. Test on target platforms (Windows, macOS, Linux)

# Output defaults
Tauri command definitions, SolidJS invoke calls, tauri.conf.json, platform build configs

# Failure handling
If IPC fails, check command is registered in Builder and invocation matches signature.
