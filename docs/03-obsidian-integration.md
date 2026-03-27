---
title: 3. Integrate Obsidian
nav_order: 3
---

# Using Copilot CLI with Obsidian
{: .fs-8 }

Your Obsidian vault is just a folder of markdown files — which means Copilot CLI can read, search, and write to it directly.
{: .fs-5 .fw-300 }

⏱️ **Estimated time: 5 minutes**

---

## What Is Obsidian?

[Obsidian](https://obsidian.md/) is a local-first markdown note-taking app. Your notes live in a **vault**, which is just a regular folder of `.md` files on your computer. No cloud account required, no proprietary format — just plain text files organized however you like.

---

## Why It Works So Well with Copilot CLI

Copilot CLI can read and write any file on your machine. Since an Obsidian vault is just a folder of markdown files, Copilot can:

- **Search your notes** — *"Find all notes mentioning Project Alpha"*
- **Summarize content** — *"Summarize the key decisions from my meeting-notes folder"*
- **Create new notes** — *"Create a note in my vault called 'Architecture Decisions' with…"*
- **Update existing notes** — *"Add a section to my onboarding.md with the setup steps we just discussed"*

No plugins or special configuration needed. Just point Copilot at your vault folder.

---

## Getting Started

### 1. Install Obsidian

Download from [obsidian.md](https://obsidian.md/) — it's free for personal use. Create a vault in a folder you can easily find (e.g., `~/Documents/Notes`).

### 2. Use Copilot CLI with Your Vault

Open Copilot CLI and reference files in your vault by path. For example:

```
Summarize all the markdown files in ~/Documents/Notes/projects/
```

```
Create a new note at ~/Documents/Notes/workshop-recap.md summarizing what I learned today
```

```
Search my vault at ~/Documents/Notes for anything related to "API design" and list the key points
```

{: .tip }
> You can use the `git-explore` skill (Module 4) to deeply analyze any folder — including your Obsidian vault — and produce a structured summary.

---

## Alternatives

Obsidian is just one option. Any markdown-based note system works the same way since Copilot CLI operates on plain files. [Logseq](https://logseq.com/), a plain folder of `.md` files, or even VS Code with markdown files all work. The key insight: **if it's a file on disk, Copilot CLI can work with it.**

---

{: .tip }
> **🎯 Try it yourself:** Point Copilot CLI at a folder of markdown files (your Obsidian vault or any notes folder) and ask: *"Read through these notes and create a summary of the main topics covered."*

---

[← Previous: Connect MCP Servers]({{ site.baseurl }}/docs/02-mcp-servers){: .btn .mr-2 }
[Next: Install Your First Skill →]({{ site.baseurl }}/docs/04-first-skill){: .btn .btn-primary }
