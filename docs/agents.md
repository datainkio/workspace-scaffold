# Agent Index

Quick reference for workspace agents (Housekeeper, Navigator, Librarian, Analyst). Agent entrypoints live in [.github/agents](../.github/agents); Copilot Chat discovers them via [copilot-agents.json](../copilot-agents.json).

## Agents
- Housekeeper — hygiene/excludes/drift; logs AIX snapshots post-context-refresh. Entrypoint: [.github/agents/housekeeper.md](../.github/agents/housekeeper.md); Prompt: [.copilot/prompts/housekeeper.prompt.md](../.copilot/prompts/housekeeper.prompt.md)
- Navigator — context concierge; assembles minimal sources and flags drift. Entrypoint: [.github/agents/navigator.md](../.github/agents/navigator.md); Prompt: [.copilot/prompts/navigator.prompt.md](../.copilot/prompts/navigator.prompt.md)
- Librarian — documentation steward; keeps docs/runbooks/decisions fresh and linked. Entrypoint: [.github/agents/librarian.md](../.github/agents/librarian.md); Prompt: [.copilot/prompts/librarian.prompt.md](../.copilot/prompts/librarian.prompt.md)
- Analyst — AIX observer; runs probes and records FRA/CR/HF/TTUO/CUS. Entrypoint: [.github/agents/analyst.md](../.github/agents/analyst.md); Prompt: [.copilot/prompts/analyst.prompt.md](../.copilot/prompts/analyst.prompt.md)

## When to Use Which
- Housekeeper: quick hygiene scan, pre-PR hygiene, post-refresh AIX snapshot, align gitignore/excludes.
- Navigator: gather authoritative context before coding/reviewing; detect drift between /context and /.copilot/context.
- Librarian: fix or update docs/runbooks/decisions, repair links, align commands to current scripts.
- Analyst: measure AIX after refresh or before releases; flag regressions.

## Copy/Paste Prompts (project-specific)
- Housekeeper: "Run a quick hygiene scan for root + frontend + backend; ensure excludes cover .obsidian/, node_modules/, frontend/_site/, backend/.sanity/; list fixes with links." 
- Housekeeper: "After refreshing context/specs, log an AIX snapshot (FRA/CR/HF/TTUO/CUS) to docs/logs with the probe tasks you used." 
- Navigator: "Assemble a minimal context pack for adding a new Eleventy collection; include routing/build outputs to avoid and any relevant decisions." 
- Navigator: "Find where Sanity schemas live and any ADRs touching CMS content; flag drift between context/ and .copilot/context if present." 
- Librarian: "Update docs/runbooks/refresh-ai-context.md after the latest build command changes; fix broken links you find." 
- Librarian: "Add a short pointer in README to the Agent Index and ensure commands match current scripts." 
- Analyst: "Run simple + complex probes (e.g., describe current frontend build outputs; outline adding a Sanity content type), score FRA/CR/HF/TTUO/CUS per specs/performance/aix.md, and add a dated note under docs/logs." 

## Key Cadence
- After every context refresh: run drift sweep, regenerate curated context (if used), then log an AIX snapshot (FRA/CR/HF/TTUO/CUS) under [docs/logs](logs/README.md#L1-L21).
- Weekly or pre-PR: run Housekeeper’s quick scan; fix excludes and doc pointers.

## Starting Points
- Context truth: [context/README.md](../context/README.md)
- Curated map: [.copilot/context/workspace-map.md](../.copilot/context/workspace-map.md)
- AIX spec: [specs/performance/aix.md](../specs/performance/aix.md)
- Refresh runbook: [docs/runbooks/refresh-ai-context.md](../docs/runbooks/refresh-ai-context.md)

## Useful Links
- Context truth: [context/README.md](../context/README.md)
- Workspace map: [.copilot/context/workspace-map.md](../.copilot/context/workspace-map.md)
- AIX spec: [specs/performance/aix.md](../specs/performance/aix.md)
- Logs folder: [docs/logs/](logs/README.md)
