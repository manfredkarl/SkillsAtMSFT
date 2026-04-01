---
title: 3. Markdown Notebook
nav_order: 3
---

# .md Notetaking
{: .fs-8 }

Markdown-based notes are the perfect companion for Copilot CLI - and we recommend Obsidian as the tool to manage them.
{: .fs-5 .fw-300 }

⏱️ **Estimated time: 5 minutes**

---

## Why Markdown Notetaking?

Copilot CLI works with files on your machine. If your notes are plain `.md` files in a folder, Copilot can read, search, create, and update them - no plugins, no APIs, no special integration. That's why we recommend a markdown-based notetaking app.

## Why We Chose Obsidian

[Obsidian](https://obsidian.md/) is a local-first markdown note-taking app. Your notes live in a **vault**, which is just a regular folder of `.md` files on your computer. No cloud account required, no proprietary format - just plain text files organized however you like.

---

## What a Vault Looks Like

A vault is just a folder. You organize it however makes sense to you - by project, by date, by topic. Here's a typical structure:

```
My-Vault/
├── Daily/
│   ├── 2026-03-27.md
│   └── 2026-03-28.md
├── Projects/
│   ├── Project-Alpha.md
│   └── Architecture-Decisions.md
├── Meeting-Notes/
│   └── 2026-03-27-Sprint-Review.md
└── Templates/
    └── meeting-template.md
```

There's no magic here - every note is a `.md` file, every folder is a regular directory. That's exactly what makes it so powerful with Copilot CLI. You can say *"read everything in my Meeting-Notes folder"* and it just works.

---

## Key Obsidian Features That Matter

Obsidian isn't just a text editor - it has a few features that turn a pile of markdown files into a connected knowledge system:

**[[Links]]** - You link notes together with `[[double brackets]]`. This creates a web of connected knowledge rather than isolated documents. When you write `[[Project-Alpha]]` in your meeting notes, Obsidian creates a clickable connection between the two - and Copilot can follow these references to understand how your ideas relate.

**Tags** - Use `#tags` to categorize notes (e.g., `#architecture`, `#decision`, `#follow-up`). Tags make it easy to find and filter notes later, and Copilot can search for them across your entire vault.

**Graph View** - Obsidian can visualize your notes as an interactive graph of connections. Nodes are notes, edges are links between them. It's a genuinely beautiful way to see how your knowledge connects - and often reveals relationships you didn't realize were there.

**Everything is plain text** - Your notes are standard markdown files on your filesystem. No vendor lock-in, no proprietary database, no subscription required to access your own writing. If you stop using Obsidian tomorrow, your notes are still right there as `.md` files.

---

## Why It's Great for Knowledge Management

Here's the real unlock: **Obsidian gives your knowledge structure, and Copilot CLI gives it intelligence.**

Build a personal knowledge base that Copilot can search, summarize, and enrich. Meeting notes, architecture decisions, code snippets, project context - all in one searchable place. Since everything is just markdown files in a folder, Copilot CLI can read, create, update, and search them naturally without any plugins or APIs. Ask it to pull insights across dozens of notes, draft a new document from existing context, or connect ideas you hadn't linked yet. It's the difference between *having* notes and *using* them.

---

## Why It Works So Well with Copilot CLI

Copilot CLI can read and write any file on your machine. Since an Obsidian vault is just a folder of markdown files, Copilot can:

- **Search your notes** - *"Find all notes mentioning Project Alpha"*
- **Summarize content** - *"Summarize the key decisions from my meeting-notes folder"*
- **Create new notes** - *"Create a note in my vault called 'Architecture Decisions' with…"*
- **Update existing notes** - *"Add a section to my onboarding.md with the setup steps we just discussed"*

No plugins or special configuration needed. Just point Copilot at your vault folder.

---

## Getting Started

### 1. Install Obsidian

Download from [obsidian.md](https://obsidian.md/) - it's free for personal use. Create a vault in a folder you can easily find (e.g., `~/Documents/Notes`).

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
> You can use the `git-explore` skill (Module 4) to deeply analyze any folder - including your Obsidian vault - and produce a structured summary.

---

## Alternatives

Obsidian is just one option. Any markdown-based note system works the same way since Copilot CLI operates on plain files. [Logseq](https://logseq.com/), a plain folder of `.md` files, or even VS Code with markdown files all work. The key insight: **if it's a file on disk, Copilot CLI can work with it.**

---

{: .tip }
> **🎯 Try it yourself:** Point Copilot CLI at a folder of markdown files (your Obsidian vault or any notes folder) and ask: *"Read through these notes and create a summary of the main topics covered."*

---

[← Previous: Connect MCP Servers]({{ site.baseurl }}/docs/02-mcp-servers){: .btn .mr-2 }
[Next: Agent Skills →]({{ site.baseurl }}/docs/04-first-skill){: .btn .btn-primary }

