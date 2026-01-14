# Concierge-Only Copilot Agents Migration Checklist (AIX-first)

## Goal
Only **Concierge** appears in the Copilot Agent dropdown, while specialist behavior remains available via prompt/modules.

## 1) Reduce discovery surface
- [ ] In `.github/agents/`, keep only `Concierge.md`
- [ ] Move other agent manifests out of `.github/agents/` (archive location suggested: `.agent/legacy-manifests/`)
- [ ] Confirm there are no other agent manifests at repo root that Copilot will discover

## 2) Convert specialists to modules
- [ ] For each specialist, ensure a corresponding module exists in `.copilot/prompts/<name>.prompt.md`
- [ ] Each module should include:
  - triggers (what it handles)
  - outputs (what it produces)
  - do/don’t constraints
  - 1–2 example calls

## 3) Consolidate registry/config
- [ ] Choose a single `copilot-agents.json` location (recommended: `.github/copilot-agents.json`)
- [ ] Remove or deprecate duplicates to avoid drift

## 4) Enforce Concierge routing contract
- [ ] Update `.github/agents/Concierge.md` to the Option C operating model
- [ ] Update `.copilot/prompts/concierge.prompt.md` to the strict module selection + blocking-question policy

## 5) Validate AIX
- [ ] Open Copilot Chat and confirm only Concierge appears
- [ ] Run 10 representative tasks and score:
  - first-pass success rate
  - number of follow-up questions
  - consistency of formatting
  - correctness of file/path guidance
- [ ] If errors cluster, strengthen module triggers and templates

## 6) Optional: safety net
- [ ] If you must keep specialist manifests (not recommended), add a 'direct-selection redirect' rule in each specialist: if not routed by Concierge token, respond with a single-line redirect.
