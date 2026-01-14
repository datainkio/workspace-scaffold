# Getting Started

This guide walks you through **starting a new project** using the Workspace Scaffold.

If you are upgrading an existing project, see `docs/migration.md` instead.

---

## Step 1: Create a new repository from the template

This scaffold is designed to be used as a **template**, not cloned directly.

- Open the Workspace Scaffold repository on GitHub
- Click **“Use this template”**
- Create a new repository for your project

This gives you a clean project with its own Git history and no technical coupling to the scaffold.

---

## Step 2: Clone your new project locally

Clone the repository you just created:

```bash
git clone <your-new-project-repo-url>
```

Open the folder in VS Code.

You are now working in **your project**, not the scaffold.

---

## Step 3: Confirm the workspace initialized correctly

When you open the project in VS Code, you should see:

- `.vscode/` (editor settings and extension recommendations)
- `context/`, `specs/`, and `docs/` folders
- Agent prompt files (Housekeeper, Migrator, etc.)
- A root `README.md` explaining the workspace

If VS Code prompts you to install recommended extensions, accept them.

---

## Step 4: Check the scaffold marker file

Each project includes a small metadata file:

```
.workspace-scaffold.json
```

This file records:
- Which scaffold version the project was created from
- When it was created
- Which parts of the workspace are scaffold‑managed

**Do not delete this file.** It enables safe upgrades later.

---

## Step 5: Start project‑specific work

From this point on:

- Treat the project as fully independent
- Add frontend, backend, research, notes, or content as needed
- Customize documentation freely unless marked as scaffold‑managed
- Commit and push changes normally

There is **no automatic syncing** with the scaffold — by design.

---

## Step 6: Applying updates in the future

As the scaffold improves over time, you can bring updates into existing projects using the **Migrator** agent.

Recommended workflow:
1. Run Migrator in **Audit mode** to see what changed
2. Review the proposed updates
3. Apply only the safe updates you want

The Migrator will:
- Never touch application code
- Never overwrite authored documentation
- Always produce a changelog

---

## Rules to remember

- ❌ Do not clone the scaffold repo to start a project
- ❌ Do not try to keep projects automatically synced
- ❌ Do not delete `.workspace-scaffold.json`
- ✅ Use the template to start new projects
- ✅ Use Migrator to upgrade intentionally

---

## Mental model

> **The scaffold is a starter kit.
> Projects are independent.
> Upgrades are intentional, not automatic.**

