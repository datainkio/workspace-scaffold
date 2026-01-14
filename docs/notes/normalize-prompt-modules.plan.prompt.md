# Copilot Prompt: Normalize Prompt Modules for Concierge (AIX-first)

You are acting as **Concierge** implementing an AIX-first migration: convert specialist “agents” into **prompt modules** and make routing deterministic and low-friction.

## Goal
Normalize every prompt module under `.copilot/prompts/` **excluding** `concierge.prompt.md` into a consistent, routing-optimized format:
- Explicit **Triggers** and **Non-triggers**
- Typed outputs with **exactly one Primary Output**
- A per-module **Blocking question (max 1, only if required)**
- A lightweight module index at `.copilot/prompts/_module-index.md`

## AIX Constraints (non-negotiable)
1) **No incremental patching of modules.** For every module rewrite, use **full-file replacement**.
2) Ensure prompt modules use **LF** line endings (avoid CRLF/BOM issues).
3) **Do not reference non-existent paths/files.** “Inputs to read first” must point only to real, stable files/paths.
4) **Limit routing surface.** Avoid generic “do everything” language; strengthen non-trigger boundaries.
5) Keep modules small, scannable, and deterministic (reduce misroutes).
6) Process modules in batches of 1–3 files per response. For each batch, output complete replacement content for each file.
7) Do not narrate. Output the full replacement content for the next 2 modules only.
8) Do not read existing module contents. Assume full overwrite is acceptable. Use only the normalized template + your best judgment for scope.
9) Batch size: rewrite max 3 modules per response.
10) No narration: output files directly, no “I’m about to…”.
11) No-read overwrite allowed: if module content exists, overwrite without attempting to preserve it.

---

## Shared Module Template (use for every module)
Use the following headings in this order:

1. `# Copilot Prompt Module: <Name>`
2. `> <One-line directive>`

3. `## Purpose`
4. `## Triggers (use when…)`
5. `## Non-triggers (do not use when…)`
6. `## Primary Output (Type: <OutputType>)`
   - Exactly one primary deliverable
   - Define structure/bullets the deliverable must include
7. `## Secondary Outputs (Optional)`
8. `## Blocking question (max 1, only if required)`
9. `## Do / Don’t`
   - `### Do`
   - `### Don’t`
10. `## Inputs to read first`
    - Only real paths; prefer “user-provided files” over assumed docs
11. `## Example calls`
    - 1–2 examples

Optional (only if needed):
- `## Non-goals` (explicitly what this module will not do)

---

## Execution Steps
### Step 1 — Inventory
- List all files in `.copilot/prompts/`.
- Mark each as:
  - **Keep as-is:** `concierge.prompt.md`
  - **Rewrite:** non-empty module needing normalization
  - **Scaffold:** empty/near-empty module needing full content

### Step 2 — Normalize non-empty modules (full-file replacement)
For each non-empty module:
- Rewrite using the Shared Module Template
- Add:
  - clear triggers and non-triggers
  - typed Primary Output with exactly one deliverable
  - ≤1 blocking question (only if truly required)
  - 1–2 example calls
- Remove:
  - `/docs/notes/**` references
  - any “Inputs to read first” that refer to non-existent files
- Ensure alternative routes mentioned in Non-triggers reference **real module names**.

### Step 3 — Fix “Inputs to read first”
Replace risky inputs with safe ones:
- Always include: `- The user request`
- If stable paths exist, include only those that are real (verify in repo)
- Otherwise: `- Any explicitly referenced files provided by the user`

### Step 4 — Scaffold empty modules (avoid routing magnets)
For empty modules:
- Create full content using the template **only if** the module has a clear, distinct job.
- If the module name is generic (e.g., planner/reviewer/implementer), choose ONE:
  - **Narrow & actionable**: strong triggers/non-triggers + specific primary output
  - **Reserved/minimal**: include explicit non-triggers so it is not selected unless the user asks explicitly

### Step 5 — Create `_module-index.md`
Create `.copilot/prompts/_module-index.md` containing, for each module:
- filename
- one-line purpose
- 3–5 top triggers (keywords/intent)
- Primary output type

Keep it short and scannable so routing can happen without reading entire modules.

### Step 6 — Consistency & AIX pass
Verify every module:
- exactly 1 primary deliverable
- ≤1 blocking question
- 1–2 example calls
- strong non-trigger boundaries
- no non-existent paths
- no “patching” language
- consistent headings/order

### Step 7 — Smoke test (AIX)
Using 10 representative prompts:
- confirm correct module selection on first pass
- count follow-up questions (should be low; max one when blocked)
- confirm outputs match declared Primary Output types

---

## Output Requirements
When you produce changes, provide:
1) A list of files changed/created
2) For each file, the **complete new content** (full-file replacement)
3) A brief AIX note: routing risks removed or improved (1–2 bullets per file)

Do not describe patch strategies. Do not attempt incremental diffs.
