---
title: 5. Create Custom Skills
nav_order: 5
---

# Creating Custom Skills
{: .fs-8 }

Write your own Agent Skills to encapsulate complex workflows into reusable, shareable instructions.
{: .fs-5 .fw-300 }

---

## Skill Anatomy

A skill is a folder containing a `SKILL.md` file with YAML frontmatter and step-by-step instructions.

```
.github/skills/my-skill/
└── SKILL.md
```

---

## Skill Locations

| Location | Path | Scope |
|:---------|:-----|:------|
| **Project (repo)** | `.github/skills/<skill-name>/SKILL.md` | Available to anyone working in the repo |
| **Personal** | `~/.copilot/skills/<skill-name>/SKILL.md` | Only affects your local machine |

---

## SKILL.md Format

Start the file with YAML metadata, followed by instructions:

```markdown
---
name: my-skill
description: Brief description of what the skill does and when to use it.
---

Step-by-step instructions for Copilot go here.
```

{: .important }
> The `description` field is critical — Copilot uses it to decide when to automatically invoke your skill based on the user's prompt.

---

## Example: GitHub Actions Debugger

Here's a practical skill for debugging failing CI/CD workflows:

```markdown
---
name: github-actions-failure-debugging
description: Guide for debugging failing GitHub Actions workflows.
---

To debug a failing GitHub Actions workflow, follow these steps:

1. Use the `list_workflow_runs` tool to find recent failed runs.
2. Use `summarize_job_log_failures` to get AI insights on log errors.
3. Retrieve full logs if needed with `get_job_logs`.
4. Identify the root cause and suggest a fix.
5. If the fix involves code changes, make the changes and verify
   locally before committing.
```

---

## Managing Skills

Use these Copilot CLI commands to manage your skills:

| Command | Description |
|:--------|:------------|
| `/skills list` | List all available skills (built-in and custom) |
| `/skills add <path>` | Add a directory of skills |
| `/skills reload` | Reload skills without restarting the CLI |
| `/skills remove <path>` | Remove a custom skill |

---

## Triggering Skills

There are two ways to invoke a skill:

### Explicit

Name the skill in your prompt:

```
Use the /my-skill to analyze this repository.
```

### Automatic

Copilot detects relevant skills based on your prompt and their descriptions. Write clear, specific descriptions to improve auto-detection accuracy.

{: .tip }
> Use the `skill-creator` skill (installed in the previous module) to help you draft and refine new skills!

---

[← Previous: Install Your First Skill]({{ site.baseurl }}/docs/04-first-skill){: .btn .mr-2 }
[Next: Voice Prompting with Handy →]({{ site.baseurl }}/docs/06-voice-prompting){: .btn .btn-primary }
