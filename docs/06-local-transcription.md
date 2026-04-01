---
title: 6. Local Transcription
nav_order: 6
---

# Voice-Driven Prompting with Handy
{: .fs-8 }

Speed up your prompting workflow by speaking commands instead of typing — fully offline and private.
{: .fs-5 .fw-300 }

---

⏱️ **Estimated time: 5–10 minutes**

Typing long, detailed prompts can slow you down — especially when you know exactly what you want to say. In this final module you'll set up Handy, an offline speech-to-text tool, so you can speak your prompts naturally and let Copilot do the rest. This ties together everything you've learned: voice-prompt a skill invocation, query your MCP servers, or dictate notes to Obsidian — all hands-free.

---

## What is Handy?

[Handy](https://handy.computer) is a free, open-source, offline speech-to-text tool. It uses OpenAI's Whisper model running locally on your machine — no audio ever leaves your device.

---

## Install Handy

Download the latest release from [handy.computer](https://handy.computer/download.html) or use a package manager:

### macOS

```bash
brew install --cask handy
```

### Windows

```bash
winget install cjpais.Handy
```

After installing, grant **microphone** and **accessibility** permissions when prompted.

{: .warning }
> **First launch is slow.** Handy needs to download a Whisper model on first run (100 MB–3 GB depending on model size). This only happens once. Subsequent launches are fast.

---

## Initial Configuration

After installing Handy, take a moment to configure it for the best experience:

1. **Open Handy** from your applications menu or system tray
2. **Set your hotkey:** Go to Settings and assign a comfortable key combo (e.g., `Ctrl+Space` or `Cmd+Shift+Space`). Pick something that won't conflict with your editor.
3. **Choose a model:** Start with **Whisper Medium** for a good balance. You can upgrade later.
4. **Test it:** Press your hotkey, say "Hello, this is a test," and release. The text should appear wherever your cursor is.

{: .tip }
> **Pro tip:** Set the hotkey to something you can press with one hand while keeping the other on your mouse — this makes dictation feel natural during your workflow.

---

## How It Works

1. **Press your hotkey** to start recording
2. **Speak your prompt** naturally — full sentences work best
3. **Release the hotkey** — Handy transcribes with Whisper and pastes into the active text field
4. **Copilot responds** to your spoken prompt

It's that simple. No cloud, no accounts, no subscriptions.

### Tips for Better Transcription

- **Speak clearly** but at a natural pace — you don't need to slow down
- **Use punctuation words** like "period", "comma", or "new line" if your model supports them
- **Pause briefly** before and after technical terms to improve accuracy
- **Spell out acronyms** the first time (e.g., say "M-C-P servers" instead of "MCP servers") until the model learns your vocabulary

---

## Troubleshooting

| Problem | Solution |
|:--------|:---------|
| No transcription output | Check that microphone permissions are granted in system settings |
| Text appears in wrong window | Make sure the target text field has focus before pressing the hotkey |
| Poor accuracy | Switch to a larger model or reduce background noise |
| Hotkey doesn't work | Check for conflicts with other apps; try a different key combo |
| High CPU usage | Switch to a smaller model or enable GPU acceleration |

---

## Privacy

{: .note }
> Handy runs **entirely on your computer**. No cloud processing, no data collection, no subscriptions.
> All audio and text stay local. It's [open source (MIT license)](https://github.com/cjpais/handy),
> making it a privacy-friendly way to speak your Copilot commands.

> **References:** [Handy website](https://handy.computer) · [Handy GitHub repo](https://github.com/cjpais/handy) · [Download page](https://handy.computer/download.html)

---

{: .tip }
> **🎯 Try it yourself:** Install Handy, configure a hotkey, and use voice to ask Copilot CLI: *"List all the skills I have installed and describe what each one does."* Then try a multi-step voice prompt: *"Find all markdown files in this project and create a summary of their contents."*

---

## 🎉 Workshop Complete!

Congratulations! You've completed the full workshop. Here's what you've accomplished:

1. ✅ Installed and authenticated Copilot CLI
2. ✅ Connected MCP servers (WorkIQ, MSX, Power BI)
3. ✅ Integrated Obsidian for note-taking
4. ✅ Installed your first Agent Skill
5. ✅ Learned to create custom skills
6. ✅ Set up voice-driven prompting

### Recommended Next Steps

- **Daily driver:** Start using Copilot CLI for your everyday tasks — the more you use it, the more workflows you'll discover to automate
- **Build team skills:** Create custom skills for your team's most common workflows and commit them to your repos
- **Connect more data:** Add MCP servers for the tools your team uses daily
- **Explore the marketplace:** Browse [skills.sh](https://skills.sh) for community-built skills
- **Share feedback:** Help improve the tools by reporting issues and suggesting features

{: .important }
> **What's next?** Start using Copilot CLI in your daily workflow! Create custom skills for your team's
> specific needs, connect additional MCP servers, and explore the
> [skills.sh marketplace](https://skills.sh) for community-built skills.

---

[← Previous: Resources & Skill Repos]({{ site.baseurl }}/docs/05-resources){: .btn .mr-2 }
[Back to Home]({{ site.baseurl }}/){: .btn .btn-primary }

