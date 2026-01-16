# Current Goals

This file is the single-source-of-truth for what matters *right now*.

Last updated: 2026-01-16

## Now
- Make the scaffold the canonical home for operational artifacts (audits, evaluations, maintenance logs) produced by Concierge.
- Reduce AIX confusion in multi-root workspaces by keeping navigation pointers stable and unambiguous (workspace map → logs convention → per-project log folder).
- Prefer “non-invasive by default” behavior: do not modify mounted projects unless explicitly authorized; when changes are authorized, keep them minimal and reversible.
- Keep logs actionable and comparable: write short, evidence-backed reports that point to exact artifacts and outcomes.

## Next
- Establish a lightweight AIX evidence loop:
	- Run a small probe set after context refreshes.
	- Record a dated snapshot in `docs/logs/` (scaffold) with outcomes and links.
- Standardize project log naming and structure across mounted repos:
	- `docs/logs/projects/<project-root>/YYYY-MM-DD-<topic>.md`
	- Include: scope, constraints used, actions taken, and follow-ups.
- Deconflict agent routing surfaces (avoid multiple competing “entrypoints” that cause wrong-agent selection).

## Not Now
- Auto-generated global inventories (a full ToC of every log file) in the workspace map.
- Heavy automation for logging/indexing until the evidence loop stabilizes and proves it saves time.
- Broad refactors inside mounted projects in the name of “cleanup” (unless explicitly approved).

## Notes
- Keep this list short (3–7 bullets per section).
- If a goal becomes stable/durable, promote it into a spec under `specs/`.

### What “good” looks like (AIX-first)

- Lower TTUO: it’s obvious where to put/find Concierge outputs.
- Lower CR: fewer ambiguous agent choices and fewer competing sources of truth.
- Higher CUS: reports consistently cite the relevant constraints, runbooks, and artifacts.
- Less drift: navigation pointers stay stable; detailed inventories live near the thing they index (or are generated).
