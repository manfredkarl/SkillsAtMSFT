---
title: Home
layout: home
nav_order: 0
---

# GitHub Copilot CLI Workshop Handbook
{: .fs-9 }

A hands-on guide to getting started with Copilot CLI, MCP integrations, and skill creation in a structured, practical way.
{: .fs-6 .fw-300 }

[Get Started]({{ site.baseurl }}/docs/01-install-authenticate){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[View on GitHub](https://github.com/manfredkarl/SkillsAtMSFT){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## What You'll Learn

This workshop walks you through everything you need to become productive with GitHub Copilot CLI and its ecosystem:

| Module | Topic | What You'll Do |
|:-------|:------|:---------------|
| 1 | [Install & Authenticate]({{ site.baseurl }}/docs/01-install-authenticate) | Install Copilot CLI and authenticate with GitHub |
| 2 | [Connect MCP Servers]({{ site.baseurl }}/docs/02-mcp-servers) | Wire up WorkIQ, MSX CRM, Power BI, and more |
| 3 | [Integrate Obsidian]({{ site.baseurl }}/docs/03-obsidian-integration) | Connect your note-taking workflow |
| 4 | [Install Your First Skill]({{ site.baseurl }}/docs/04-first-skill) | Add agent skills from skills.sh |
| 5 | [Create Custom Skills]({{ site.baseurl }}/docs/05-custom-skills) | Write your own SKILL.md files |
| 6 | [Voice Prompting with Handy]({{ site.baseurl }}/docs/06-voice-prompting) | Speak your commands instead of typing |

---

## Workshop Outline

```
1. Install Copilot CLI (npm or brew)
2. Authenticate / Run copilot login
3. Run copilot --yolo (full permissions)
4. Configure MCP servers (WorkIQ, MSX, PowerBI, etc.)
5. Add first Agent Skill (skill-creator)
6. Integrate Obsidian & enable Handy voice input
```

{: .note }
> This guide is based on official documentation and the latest resources including
> [GitHub Copilot CLI docs](https://docs.github.com/copilot/how-tos/set-up/install-copilot-cli),
> [WorkIQ](https://github.com/microsoft/work-iq-mcp), and
> [skills.sh](https://skills.sh).
> Security considerations (especially when using `--yolo`) are highlighted throughout.
