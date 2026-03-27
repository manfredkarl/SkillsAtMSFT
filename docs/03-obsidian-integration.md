---
title: 3. Integrate Obsidian
nav_order: 3
---

# Integrating Note-Taking with Obsidian
{: .fs-8 }

Use a local markdown note-taking app to record insights and context for your Copilot sessions.
{: .fs-5 .fw-300 }

⏱️ **Estimated time: 5–10 minutes**

A great AI workflow captures context and decisions as you go. In this module you'll connect Copilot CLI to Obsidian — a local-first markdown editor — so Copilot can read your notes, manage your tasks, and help you build a personal knowledge base without anything leaving your machine.

---

## Why Obsidian?

[Obsidian](https://obsidian.md/) is a powerful, privacy-first markdown editor that stores all your notes as plain `.md` files on your local disk. Combined with Copilot, it becomes an AI-augmented knowledge base where you can:

- **Search across hundreds of notes** using natural language instead of keywords
- **Auto-generate daily summaries** from meeting notes and tasks
- **Build linked knowledge graphs** with AI-assisted connections between topics
- **Keep everything private** — no cloud dependency unless you choose to sync

---

## Setup Obsidian + Copilot

### 1. Install Obsidian

If you don't already have Obsidian, download it from [obsidian.md](https://obsidian.md/) — it's free for personal use. Create a vault (or open an existing one) in a folder you can easily find.

### 2. Install the Obsidian Copilot Plugin

1. Open Obsidian → **Settings** → **Community Plugins**
2. Click **Browse** and search for **Copilot**
3. Click **Install**, then **Enable**
4. Configure the plugin settings — you may need to provide your GitHub token

The plugin provides an in-vault AI assistant, allowing chat-based search of your notes and integration with Copilot's agents.

{: .note }
> **Community plugins disabled?** Go to **Settings → Community Plugins** and toggle off **Restricted Mode**. You'll see a warning — this is safe for trusted plugins like Copilot.

### 3. Enable Daily Notes (Recommended)

For the best experience, enable Obsidian's built-in **Daily Notes** plugin:

1. Go to **Settings → Core Plugins**
2. Enable **Daily Notes**
3. Configure your preferred date format and template

Daily notes give Copilot a natural place to log insights, action items, and session summaries.

---

## Available CLI Tools

Copilot's Obsidian integration adds CLI tools to access your vault (desktop only):

| Tool | Description | Example Use |
|:-----|:------------|:------------|
| `obsidianDailyNote` | Read or append to today's daily note | Log meeting action items |
| `obsidianTasks` | List all tasks across your vault | Review open to-dos |
| `obsidianLinks` | List backlinks for a note | Discover related topics |

You can use these directly in Copilot CLI after enabling them:

```
copilot> /tool obsidianDailyNote
copilot> /tool obsidianTasks
```

{: .important }
> **Obsidian must be running** on your desktop for these tools to work. The CLI communicates with Obsidian's local REST API, which is only active when the app is open.

---

## Example Use Cases

Keep your Obsidian vault open while working with Copilot. Try prompts like:

- *"Summarize today's meeting notes and append a decision list"*
- *"What tasks are still open in my vault?"*
- *"Create a new note summarizing the architecture discussion"*
- *"Find all notes related to Project Alpha and list the key decisions"*
- *"Add a task to my daily note: Review PR #42 before EOD"*

### A Typical Workflow

1. **Morning:** Ask Copilot to read your daily note and summarize yesterday's open tasks
2. **During meetings:** Dictate notes using Handy (Module 6) and let Copilot append them
3. **After work:** Ask Copilot to generate a summary of the day and create tomorrow's task list

{: .tip }
> All notes remain local and private — nothing is sent to the cloud unless you explicitly choose to sync.

---

## Troubleshooting

| Problem | Solution |
|:--------|:---------|
| Tools return "connection refused" | Make sure Obsidian is running on your desktop |
| Daily note not found | Enable the Daily Notes core plugin and create today's note |
| Plugin not showing in search | Toggle off Restricted Mode in Community Plugins settings |
| Copilot can't find your vault | Ensure your vault path is accessible — avoid network drives |

---

## Alternatives

Any markdown-based note app works similarly. Copilot CLI can edit any plaintext file via shell tools — for example:

```bash
code filename.md    # Open in VS Code
```

Other popular options include [Logseq](https://logseq.com/), [Notion](https://notion.so) (with API access), or even a simple folder of `.md` files. The key is having a structured place to capture context, decisions, and follow-ups as you work.

---

{: .tip }
> **🎯 Try it yourself:** Open your Obsidian vault and create a daily note for today. Then ask Copilot CLI: *"Append a section called 'Workshop Notes' to my daily note with three things I've learned so far."* Verify the content appears in Obsidian.

---

[← Previous: Connect MCP Servers]({{ site.baseurl }}/docs/02-mcp-servers){: .btn .mr-2 }
[Next: Install Your First Skill →]({{ site.baseurl }}/docs/04-first-skill){: .btn .btn-primary }
