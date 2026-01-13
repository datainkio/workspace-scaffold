# Runbook: Refresh AI Context & Indexes

- **Owner:** DX Team
- **Last validated:** 2026-01-13
- **Preconditions:** Local repo clean; access to main branch; editors honor `.vscode/settings.json` excludes.

## Steps
1) Pull latest: `git pull origin main`.
2) Review for truth updates: scan `/context` and `/specs` for changes; ensure ADRs in `/docs/decisions` reflect any new choices.
3) Sync derived context (if used): regenerate any `.copilot/context` or agent cache files to mirror `/context` and `/specs` summaries.
4) Validate structure: confirm required folders exist (`/context`, `/specs`, `/docs/decisions`, `/docs/runbooks`, `/docs/notes`), and excludes cover `node_modules`, build outputs, `.obsidian`, caches.
5) Smoke test agent hints: open README files in `/context`, `/specs`, `/docs/decisions`, `/docs/runbooks`; ensure instructions are current and non-contradictory.
6) Commit and push: include ADR/runbook updates if made.

## Expected Outputs & Checks
- Excludes remain in `.vscode/settings.json` and `.gitignore` and match the scaffold goals.
- ADRs align with `/context` and `/specs`; no conflicting guidance across folders.
- Agents see the latest context (regenerated summaries/caches where applicable).

## Rollback / Undo
- If regenerated context introduces issues, revert the cache/snapshot files and reopen the last known good versions from main.
- If folder structure was altered incorrectly, restore from git and re-apply the scaffold layout.

## Comms Template
- "Refreshed AI context/indexes for workspace scaffold. Synced `/context`, `/specs`, ADRs, runbooks; validated excludes. Please pull main to pick up updates."
