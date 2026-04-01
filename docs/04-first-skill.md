---
title: 4. Agent Skills
nav_order: 4
---

# Agent Skills — Install & Create
{: .fs-8 }

Install the skill-creator, then use it right away to build your first custom skill.
{: .fs-5 .fw-300 }

⏱️ **Estimated time: 10–15 minutes**

Skills are what make Copilot truly customizable. Instead of writing the same complex prompts over and over, you package them into reusable skill files (`SKILL.md`) that Copilot loads automatically. In this module you'll install the skill-creator and immediately put it to work.

---

## What Are Agent Skills?

Skills are structured instruction files that give Copilot domain-specific capabilities. Think of them as **expert playbooks** — each skill teaches Copilot a specific workflow. They can be:

- **Installed from the community** via [skills.sh](https://skills.sh)
- **Created custom** for your team using the skill-creator
- **Shared** across repositories and teams via Git

---

## Install the Skill Creator

Run this in your terminal or paste it directly into GitHub Copilot CLI:

```bash
npx skills add anthropics/skills --skill skill-creator
```

You'll see output confirming the skill was downloaded and placed in your `.github/skills/` directory.

### Verify Installation

```
/skills list
```

You should see `skill-creator` in the list. You can also type `/skill` and Copilot will auto-suggest relevant installed skills.

{: .warning }
> **Skill not showing up?** Make sure you ran the install command from the root of a Git repository. Skills are stored in `.github/skills/` relative to your project root.

---

## Create Your First Skill

Now let's use the skill-creator right away. Here's a practical example — creating a skill that prepares daily stand-up summaries:

```
Use the skill-creator to create a new skill called "standup-prep" that
prepares a daily stand-up summary. It should check recent git commits,
open pull requests by the current user, and today's calendar if WorkIQ
is available. Format the output as Yesterday / Today / Blockers.
```

The skill-creator will:

1. **Ask clarifying questions** if it needs more detail
2. **Generate a `SKILL.md` file** with proper frontmatter and step-by-step instructions
3. **Save it** to `.github/skills/standup-prep/SKILL.md`

That's it — your skill is ready to use.

---

## Try Your New Skill

Test it by asking Copilot a natural question:

```
What did I work on yesterday?
```

Copilot detects the `standup-prep` skill from its description and follows the instructions automatically. If it doesn't trigger, refine the description:

```
Use the skill-creator to improve the description of my standup-prep
skill so it triggers when I ask about daily status or what I did yesterday.
```

---

## More Skill Ideas

Here are a few more skills worth creating:

- **`debug-ci`** — Diagnose failing GitHub Actions workflows by pulling logs and summarizing errors
- **`pr-review-checklist`** — Run through your team's code review checklist on a pull request diff
- **`format-release-notes`** — Generate release notes from merged PRs since the last tag

For each one, just describe what you want in plain English and let the skill-creator handle the rest.

---

## Organizing Your Skills

Before you install a dozen skills, think about **where** they should live:

| Where | Path | Best for | Install flag |
|:------|:-----|:---------|:-------------|
| **Global** | `~/.copilot/skills/` | Personal productivity, always available | `npx skills add ... -g` |
| **Project** | `.github/skills/` | Team workflows, shared via Git | `npx skills add ...` (default) |

**Rule of thumb:** *"Would I use this in every repo?"* → Global. *"Is this specific to this team/project?"* → Project.

{: .note }
> Skills created at the project level travel with the repo — when a colleague clones it, they automatically get your team's skills.

---

## Explore More Skills

```bash
# List available skills in a repository
npx skills add anthropics/skills --list

# Install globally (available across all projects)
npx skills add anthropics/skills --skill pptx -g

# Search for skills
npx skills find "code review"
```

{: .tip }
> **🎯 Try it yourself:** Use the skill-creator to build a `standup-prep` skill, then test it by asking Copilot: *"What did I work on yesterday?"*

> **References:** [About agent skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) · [Skills CLI](https://github.com/vercel-labs/skills) · [skills.sh marketplace](https://skills.sh)

---

[← Previous: Markdown Notebook]({{ site.baseurl }}/docs/03-obsidian-integration){: .btn .mr-2 }
[Next: Voice Prompting with Handy →]({{ site.baseurl }}/docs/05-voice-prompting){: .btn .btn-primary }
