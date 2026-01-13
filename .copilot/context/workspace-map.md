# Workspace Map
This file describes where everything lives (frontend/backend/root) and what each folder contains. Focus: keep AI agents oriented and fast.

## Canonical Context (source of truth)
- [context/README.md](context/README.md) — canonical layer description. Expected but missing: `context/decisions.md`, `context/current-goals.md` (add soon so agents have goals/ADRs).

## Specs (contracts)
- [specs/README.md](specs/README.md) — folder purpose.
- Empty spec stubs to populate: [specs/architecture.md](specs/architecture.md), [specs/components.md](specs/components.md), [specs/routes-and-content.md](specs/routes-and-content.md), [specs/cms-schema-contract.md](specs/cms-schema-contract.md), [specs/animation-system.md](specs/animation-system.md).

## Docs (narrative, non-canonical)
- [docs/README.md](docs/README.md) — explains intent. Subfolders `docs/decisions/`, `docs/notes/`, `docs/runbooks/`, `docs/logs/` exist; add runbooks for repeatable tasks and keep logs for hygiene/AIX snapshots.

## Scripts
- [scripts/README.md](scripts/README.md) — guidance; no scripts yet.

## Assets & Data
- [assets/](assets/) and [data/](data/) exist; both empty. Add manifests when populated so agents can locate media/data fast.

## Workspace Config
- [workspace_template.code-workspace](workspace_template.code-workspace) — VS Code workspace definition.
- Root [README.md](README.md) — describes this as language-agnostic scaffold and Obsidian setup.

## Agent Roles
- Housekeeper: hygiene, excludes, drift sweeps, AIX snapshot logging after context refreshes.
- Navigator: context concierge; assembles minimal source bundle and flags drift.
- Librarian: documentation steward; keeps runbooks/decisions/notes fresh and linked.
- Analyst: AIX observer; runs probes and records FRA/CR/HF/TTUO/CUS into logs.

## Agent Notes / Next AIX actions
- Create `context/current-goals.md` and `context/decisions.md` to anchor priorities/ADRs.
- Fill core specs starting with `specs/architecture.md` and `specs/components.md` to reduce ambiguity for generation.
- Add initial runbooks in `docs/runbooks/` for common workflows; link any scripts once added.
- Schedule AIX snapshots after each context refresh; store under `docs/logs/`.