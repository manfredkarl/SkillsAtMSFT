---
title: 3. Integrate Obsidian
nav_order: 3
---

# Integrating Note-Taking with Obsidian
{: .fs-8 }

Use a local markdown note-taking app to record insights and context for your Copilot sessions.
{: .fs-5 .fw-300 }

---

## Why Obsidian?

[Obsidian](https://obsidian.md/) is a powerful, privacy-first markdown editor that stores all your notes locally. Combined with Copilot, it becomes an AI-augmented knowledge base.

---

## Setup Obsidian + Copilot

### Install the Obsidian Copilot Plugin

1. Open Obsidian → **Settings** → **Community Plugins**
2. Search for **Copilot** and install it
3. Enable the plugin

The plugin provides an in-vault AI assistant, allowing chat-based search of your notes and integration with Copilot's agents.

---

## Available CLI Tools

Copilot's Obsidian integration adds CLI tools to access your vault (desktop only):

| Tool | Description |
|:-----|:------------|
| `obsidianDailyNote` | Read or append to today's daily note |
| `obsidianTasks` | List all tasks across your vault |
| `obsidianLinks` | List backlinks for a note |

You can use these directly in Copilot CLI after enabling them:

```
copilot> /tool obsidianDailyNote
copilot> /tool obsidianTasks
```

---

## Example Use Cases

Keep your Obsidian vault open while working with Copilot. Try prompts like:

- *"Summarize today's meeting notes and append a decision list"*
- *"What tasks are still open in my vault?"*
- *"Create a new note summarizing the architecture discussion"*

{: .tip }
> All notes remain local and private — nothing is sent to the cloud unless you explicitly choose to sync.

---

## Alternatives

Any markdown-based note app works similarly. Copilot CLI can edit any plaintext file via shell tools — for example:

```bash
code filename.md    # Open in VS Code
```

The key is having a structured place to capture context, decisions, and follow-ups as you work.

---

[← Previous: Connect MCP Servers]({{ site.baseurl }}/docs/02-mcp-servers){: .btn .mr-2 }
[Next: Install Your First Skill →]({{ site.baseurl }}/docs/04-first-skill){: .btn .btn-primary }
