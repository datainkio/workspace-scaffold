# 🏗️ Workspace Scaffold

A lightweight scaffold for creating **VS Code workspaces** with:
- solid repo hygiene (ignores, structure)
- better Copilot/agent ergonomics (routing, context)
- documentation patterns you can reuse

## Getting Started

This repository is a **reusable VS Code workspace scaffold**.

It is intended to be used as a **template** when starting a new project — not cloned and detached.

Important: Do not regenerate agent instructions (i.e. the button you get in the initial dialog for Copilot Chat). This workspace uses a custom Concierge + module routing system calibrated for AIX.

**To start a new project:**
1. Create a new repository using this repo as a **template**
2. Clone your new project locally
3. Follow the step-by-step guide in `docs/getting-started.md`

> **Important:** Do not clone this repository directly to start a project.
> Use the Migrator agent to apply scaffold updates to existing projects.

## What this repo does (and doesn’t)

- ✅ Maintains hygiene + AIX performance for the workspace
- ✅ Provides templates and doc structure for consistent project documentation
- ❌ Does not implement your product code (push that into project repos)

## Workspace actions

- [New Project](command:workbench.action.tasks.runTask?%22New%20Project%22) (POC task)
- [Agent Index](docs/agents.md)

## Docs

- Getting started: `docs/getting-started.md`
- Docs hub: `docs/README.md`

## Tooling

This scaffold is intentionally **tool-agnostic**. Use what your project needs.

### Mermaid

Mermaid is great for lightweight diagrams in Markdown. Example prompt:

> “Review the XYZ package. Create a Mermaid diagram illustrating the initialization sequence.”

### Obsidian

The workspace includes an `.obsidian/` folder so the repo can be opened as an Obsidian vault.

- If you don’t use Obsidian, delete `.obsidian/` locally.
- If you do use Obsidian, keep notes wherever you like (committed Markdown, Obsidian Sync, iCloud, etc.).
- This repo defaults to **not tracking** `.obsidian/` in Git (to avoid editor state creep).
