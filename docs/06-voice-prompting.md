---
title: 6. Voice Prompting
nav_order: 6
---

# Voice-Driven Prompting with Handy
{: .fs-8 }

Speed up your prompting workflow by speaking commands instead of typing — fully offline and private.
{: .fs-5 .fw-300 }

---

## What is Handy?

[Handy](https://handy.computer) is a free, open-source, offline speech-to-text tool. It uses OpenAI's Whisper model running locally on your machine — no audio ever leaves your device.

---

## Install Handy

Download the latest release from [handy.computer](https://handy.computer/download.html) or use a package manager:

### macOS

```bash
brew install handy
```

### Windows

```bash
winget install handy
```

After installing, grant **microphone** and **accessibility** permissions when prompted.

---

## How It Works

1. **Configure a hotkey** (e.g., `Ctrl+Space`) to start/stop recording
2. **Press and speak** your prompt
3. **Release** — Handy transcribes with Whisper and pastes into the active text field
4. **Copilot responds** to your spoken prompt

It's that simple. No cloud, no accounts, no subscriptions.

---

## Example Voice Prompts

Here are some prompts you might speak into Copilot CLI:

| Voice Prompt | What Copilot Does |
|:-------------|:------------------|
| *"Show me all TODO comments in the repository"* | Searches codebase for TODOs |
| *"Generate unit tests for the function in utils/file.js"* | Creates test file |
| *"Use the skill-creator to draft a new skill for formatting Markdown"* | Invokes the skill-creator |
| *"What did I plan for today's meeting? Summarize my daily note in Obsidian"* | Queries Obsidian via MCP |
| *"Check the status of my MCP servers"* | Runs `/mcp status` |

---

## Supported Models

Handy supports multiple transcription models:

| Model | Best For |
|:------|:---------|
| **Whisper Small** | Fast transcription, lower accuracy |
| **Whisper Medium** | Good balance of speed and accuracy |
| **Whisper Turbo** | Optimized for real-time use |
| **Whisper Large** | Highest accuracy, requires GPU |
| **Parakeet V3** | Efficient CPU-based transcription |

{: .tip }
> If you have a GPU, enable GPU acceleration in Handy's settings for near-instant transcription with the Large model.

---

## Privacy

{: .note }
> Handy runs **entirely on your computer**. No cloud processing, no data collection, no subscriptions.
> All audio and text stay local. It's [open source (MIT license)](https://github.com/cjpais/handy),
> making it a privacy-friendly way to speak your Copilot commands.

---

## 🎉 Workshop Complete!

Congratulations! You've completed the full workshop. Here's what you've accomplished:

1. ✅ Installed and authenticated Copilot CLI
2. ✅ Connected MCP servers (WorkIQ, MSX, Power BI)
3. ✅ Integrated Obsidian for note-taking
4. ✅ Installed your first Agent Skill
5. ✅ Learned to create custom skills
6. ✅ Set up voice-driven prompting

{: .important }
> **What's next?** Start using Copilot CLI in your daily workflow! Create custom skills for your team's
> specific needs, connect additional MCP servers, and explore the
> [skills.sh marketplace](https://skills.sh) for community-built skills.

---

[← Previous: Create Custom Skills]({{ site.baseurl }}/docs/05-custom-skills){: .btn .mr-2 }
[Back to Home]({{ site.baseurl }}/){: .btn .btn-primary }
