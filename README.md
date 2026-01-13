# 🏗️ Workspace Scaffold
This folder serves provides a scaffold for creating new VS Code workspaces. The goals are to improve the developer experience by maintaining:
* good workspace hygiene,
* optimal agent performance,
* meaningful documentation

## Implementation
My preference is use this as the foundation for a single-root workspace. Folders like /frontend and /backend *can* be included, but good repo hygiene calls for maintaining them separately and just referencing them in the workspace via *add folder*.

## Boundaries
Agents here maintain hygiene and AIX perf only—defer coding to project-specific agents.

## Workspace actions
- [New Project](command:workbench.action.tasks.runTask?%22New%20Project%22)
- [Agent Index](docs/agents.md)
- Clean House
- Reload Window (for new agents)

## Tooling
The workspace is designed with a tool-agnostic directory structure. 

### Integrations
#### Mermaid
Mermaid is a tidy little tool designed to build charts, graphs, and diagrams from markdown files. Good for ideating, good for documenting, and good for communicating. Especially nice when you tell Copilot: "Review the XYZ package. Create a Mermaid diagram illustrating the initialization sequence..."
#### 📓Obsidian
Obsidian is another handly little tool for working with markdown. The workspace root comes configured as an Obsidian vault. Not a fan of Obsidian? No worries. Just ignore or delete the .obsidian folder.

Keep your notes in sync with Git or an Obsidian account or, if you're feeling daring, iCloud or GDrive.

The scaffold integrates with Obsidian not through an extension but by including default a default vault directory. 

The Obsidian instance comes pre-configured with an ignore list to optimize the DX when working within the Obsidian app by reducing the amount of noise coming from folders (e.g. Node, 11ty, Sanity, ComfyUI, etc.)

These community plugins are installed and enabled by default:
- [Dataview](https://github.com/Obsidian-Dataview/dataview)
- [Templater](https://github.com/SilentVoid13/Templater)
- [Tasks](https://github.com/obsidian-tasks-group/obsidian-tasks)
- [Kanban](https://github.com/mgmeyers/obsidian-kanban)

### Extensions
#### Core
#### Development
Sanity.io
SVG
Nunjucks
Github Copilot Chat

#### Publishing
Deploy to Github Pages
Markdown PDF

#### Developer Experience
npm intellisense
Tailwind CSS Intellisense
Prettier
Material Icon Theme
Figma for VS Code
Mermaid Preview
Markdown Preview Enhanced
Git Graph


