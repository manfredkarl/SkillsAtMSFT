---
title: 5. Create Custom Skills
nav_order: 5
---

# Creating Custom Skills
{: .fs-8 }

Write your own Agent Skills to encapsulate complex workflows into reusable, shareable instructions.
{: .fs-5 .fw-300 }

⏱️ **Estimated time: 10–15 minutes**

Now that you've installed a community skill, it's time to create your own. Custom skills let you encode your team's best practices, standard operating procedures, and domain expertise into reusable instructions that any team member can invoke. This is where Copilot becomes truly tailored to your organization.

---

## Skill Anatomy

A skill is a folder containing a `SKILL.md` file with YAML frontmatter and step-by-step instructions.

```
.github/skills/my-skill/
└── SKILL.md
```

The folder name becomes the skill's identifier, and the `SKILL.md` file contains everything Copilot needs to execute it.

---

## Skill Locations

| Location | Path | Scope | Use When |
|:---------|:-----|:------|:---------|
| **Project (repo)** | `.github/skills/<skill-name>/SKILL.md` | Available to anyone working in the repo | Team-shared workflows |
| **Personal** | `~/.copilot/skills/<skill-name>/SKILL.md` | Only affects your local machine | Personal productivity |

{: .note }
> **Project skills travel with the repo.** When a colleague clones your repository, they automatically get all project-level skills. This makes skills a great way to standardize workflows across your team.

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
> The `description` field is critical — Copilot uses it to decide when to automatically invoke your skill based on the user's prompt. Be specific about **what** the skill does and **when** it should trigger.

### Writing Effective Descriptions

Your skill's description determines how reliably Copilot activates it. Compare these examples:

| ❌ Vague | ✅ Specific |
|:---------|:-----------|
| `"Helps with PRs"` | `"Reviews pull request diffs for security vulnerabilities, SQL injection, and credential exposure. Use when reviewing PRs or when asked about code security."` |
| `"Does testing"` | `"Generates unit tests for TypeScript functions using Jest. Covers happy paths, edge cases, and error handling."` |

### Writing Effective Instructions

The body of your `SKILL.md` should contain clear, numbered steps. Write instructions as if you're teaching a capable junior developer:

- **Be explicit** about which tools to use (e.g., `grep`, `git`, specific MCP tools)
- **Specify output format** if you want consistent results (e.g., "output as a markdown table")
- **Include guardrails** to prevent unwanted behavior (e.g., "do not modify files outside the `src/` directory")
- **Add examples** of expected input/output when helpful

---

## Example: GitHub Actions Debugger

Here's a practical skill for debugging failing CI/CD workflows:

```markdown
---
name: github-actions-failure-debugging
description: Guide for debugging failing GitHub Actions workflows.
  Use when a CI/CD pipeline fails, when asked about workflow errors,
  or when troubleshooting build/test failures in GitHub Actions.
---

To debug a failing GitHub Actions workflow, follow these steps:

1. Use the `list_workflow_runs` tool to find recent failed runs.
2. Use `summarize_job_log_failures` to get AI insights on log errors.
3. Retrieve full logs if needed with `get_job_logs`.
4. Identify the root cause and suggest a fix.
5. If the fix involves code changes, make the changes and verify
   locally before committing.
```

## Example: Daily Stand-Up Prep

Here's a simpler skill for personal productivity:

```markdown
---
name: standup-prep
description: Prepares a daily stand-up summary by reviewing
  recent git commits, open PRs, and calendar. Use when asked
  about stand-up, daily status, or "what did I do yesterday".
---

Prepare a stand-up summary:

1. Run `git log --oneline --since="yesterday"` to find recent commits.
2. Check open pull requests authored by the current user.
3. If WorkIQ is available, check today's calendar for relevant meetings.
4. Format the output as:
   - **Yesterday:** [completed items]
   - **Today:** [planned items based on open PRs and meetings]
   - **Blockers:** [any failed CI or unresolved review comments]
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

{: .tip }
> After editing a `SKILL.md` file, run `/skills reload` so Copilot picks up the changes without restarting.

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

### Testing Your Skill

After creating a skill, test it to make sure it triggers correctly:

1. **Explicit test:** Ask Copilot to *"use my-skill to do X"* and verify it follows the instructions
2. **Auto-trigger test:** Ask a question that matches the skill's description without naming it — does Copilot pick it up?
3. **Edge case test:** Try prompts that are similar but shouldn't trigger the skill — does it stay quiet?

{: .warning }
> **Common pitfall:** If your skill never auto-triggers, your description is probably too vague. If it triggers when it shouldn't, your description is too broad. Iterate on the description until the trigger behavior feels right.

---

## Best Practices

- **One skill per task.** Keep skills focused — a skill that does too many things is hard to trigger reliably.
- **Version control your skills.** Since project skills live in `.github/skills/`, they're automatically tracked by Git.
- **Use the skill-creator.** The meta-skill from Module 4 can help you draft and refine new skills.
- **Share with your team.** When you build a useful skill, commit it to the repo so everyone benefits.

{: .tip }
> Use the `skill-creator` skill (installed in the previous module) to help you draft and refine new skills!

---

{: .tip }
> **🎯 Try it yourself:** Create a custom skill called `standup-prep` that prepares a daily stand-up summary from your recent Git commits. Create the file at `.github/skills/standup-prep/SKILL.md`, then test it by asking Copilot: *"What did I work on yesterday?"*

---

[← Previous: Install Your First Skill]({{ site.baseurl }}/docs/04-first-skill){: .btn .mr-2 }
[Next: Voice Prompting with Handy →]({{ site.baseurl }}/docs/06-voice-prompting){: .btn .btn-primary }
