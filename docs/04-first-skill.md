---
title: 4. Install Your First Skill
nav_order: 4
---

# Installing Your First Agent Skill
{: .fs-8 }

Agent Skills are reusable instructions that teach Copilot to perform specialized tasks. Install your first one in seconds.
{: .fs-5 .fw-300 }

⏱️ **Estimated time: 5 minutes**

Skills are what make Copilot truly customizable. Instead of writing the same complex prompts over and over, you package them into reusable skill files that Copilot loads automatically. In this module you'll install your first skill and see how it changes what Copilot can do.

---

## What Are Agent Skills?

Skills are structured instruction files (`SKILL.md`) that give Copilot domain-specific capabilities. Think of them as **expert playbooks** — each skill teaches Copilot a specific workflow with step-by-step instructions. They can be:

- **Installed from the community** via [skills.sh](https://skills.sh) — a growing marketplace of pre-built skills
- **Created custom** for your team or project (covered in the next module)
- **Shared** across repositories and teams via Git

When you ask Copilot to do something, it checks all installed skills and automatically uses the most relevant one based on its description. You can also invoke skills explicitly by name.

---

## Install the Skill Creator

As your first skill, add the **Skill Creator** — a meta-skill that helps you build new skills. In your terminal, run:

```bash
npx skills add vercel-labs/agent-skills --skill skill-creator
```

You'll see output confirming the skill was downloaded and placed in your `.github/skills/` directory.

{: .note }
> This downloads the skill definitions into Copilot's skills folder. Browse more skills at [skills.sh](https://skills.sh).

### What Just Happened?

The `npx skills add` command:
1. Fetched the `skill-creator` skill from the `vercel-labs/agent-skills` repository
2. Created a `.github/skills/skill-creator/` directory in your project
3. Placed a `SKILL.md` file inside with instructions Copilot will follow

---

## Verify Installation

In Copilot CLI, check your installed skills:

```
/skills list
```

Or simply ask:

```
What skills do you have?
```

You should see `skill-creator` in the list along with any built-in skills.

{: .warning }
> **Skill not showing up?** Make sure you ran the install command from the root of a Git repository. Skills are stored in `.github/skills/` relative to your project root. If you installed from a different directory, Copilot won't find them.

---

## Use the Skill

To invoke Skill Creator, prompt Copilot with it. For example:

```
Use the skill-creator to draft a new skill for automating GitHub issue triage.
```

Copilot will follow the Skill Creator instructions to scaffold a new skill for you, including the YAML frontmatter, a clear description, and step-by-step instructions.

### More Invocation Examples

```
Create a skill that reviews pull requests for security issues
```

```
Use skill-creator to build a skill for generating release notes from commit history
```

```
Draft a skill for onboarding new team members to our codebase
```

---

## Explore More Skills

Browse and install additional skills:

```bash
# List available skills in a repository
npx skills add vercel-labs/agent-skills --list

# Install a specific skill
npx skills add vercel-labs/agent-skills --skill frontend-design

# Install globally (available across all projects)
npx skills add vercel-labs/agent-skills --skill skill-creator -g

# Search for skills
npx skills find "code review"
```

### Popular Skills to Try

| Skill | What It Does |
|:------|:-------------|
| `skill-creator` | Helps you create new skills (you just installed this!) |
| `frontend-design` | Guides frontend UI/UX implementation |
| `git-explore` | Deep-dives into repos and produces documentation |
| `code-review` | Reviews code changes for bugs and security issues |

{: .tip }
> Skills are placed in your `.github/skills/` directory by default. Copilot auto-detects and loads them when relevant to your tasks. Global skills (installed with `-g`) go to `~/.copilot/skills/` and are available in all projects.

---

{: .tip }
> **🎯 Try it yourself:** Install the `skill-creator` skill, then ask Copilot: *"Use the skill-creator to build a skill that summarizes a GitHub repository's README and lists its key dependencies."* Review the generated `SKILL.md` file and see how it's structured.

> **References:** [About agent skills](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills) · [Skills CLI](https://github.com/vercel-labs/skills) · [skills.sh marketplace](https://skills.sh)

---

[← Previous: Integrate Obsidian]({{ site.baseurl }}/docs/03-obsidian-integration){: .btn .mr-2 }
[Next: Create Custom Skills →]({{ site.baseurl }}/docs/05-custom-skills){: .btn .btn-primary }
