---
title: 4. Install Your First Skill
nav_order: 4
---

# Installing Your First Agent Skill
{: .fs-8 }

Agent Skills are reusable instructions that teach Copilot to perform specialized tasks. Install your first one in seconds.
{: .fs-5 .fw-300 }

---

## What Are Agent Skills?

Skills are structured instruction files (`SKILL.md`) that give Copilot domain-specific capabilities. They can be:

- **Installed from the community** via [skills.sh](https://skills.sh)
- **Created custom** for your team or project
- **Shared** across repositories and teams

---

## Install the Skill Creator

As your first skill, add the **Skill Creator** — a meta-skill that helps you build new skills. In your terminal, run:

```bash
npx skills add vercel-labs/agent-skills --skill skill-creator
```

{: .note }
> This downloads the skill definitions into Copilot's skills folder. Browse more skills at [skills.sh](https://skills.sh).

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

You should see `skill-creator` in the list.

---

## Use the Skill

To invoke Skill Creator, prompt Copilot with it. For example:

```
Use the skill-creator to draft a new skill for automating GitHub issue triage.
```

Copilot will follow the Skill Creator instructions to scaffold a new skill for you.

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

{: .tip }
> Skills are placed in your `.github/skills/` directory by default. Copilot auto-detects and loads them when relevant to your tasks.

---

[← Previous: Integrate Obsidian]({{ site.baseurl }}/docs/03-obsidian-integration){: .btn .mr-2 }
[Next: Create Custom Skills →]({{ site.baseurl }}/docs/05-custom-skills){: .btn .btn-primary }
