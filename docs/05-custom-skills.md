---
title: 5. Create Custom Skills
nav_order: 5
---

# Creating Custom Skills
{: .fs-8 }

Use the skill-creator to build custom skills that teach Copilot your team's workflows.
{: .fs-5 .fw-300 }

⏱️ **Estimated time: 10–15 minutes**

Custom skills are instruction files that teach Copilot how to perform specialized tasks — things like debugging CI pipelines, prepping stand-up notes, or enforcing your team's code review checklist. Instead of writing these files by hand, the easiest way to create one is with the **skill-creator** skill you installed in the previous module.

---

## Create a Skill with skill-creator

Let's walk through a practical example: creating a skill that prepares a daily stand-up summary from your recent Git activity.

In Copilot CLI, type:

```
Use the skill-creator to create a new skill called "standup-prep" that
prepares a daily stand-up summary. It should check recent git commits,
open pull requests by the current user, and today's calendar if WorkIQ
is available. Format the output as Yesterday / Today / Blockers.
```

The skill-creator will:

1. **Ask clarifying questions** if it needs more detail about the workflow
2. **Generate a `SKILL.md` file** with proper frontmatter (name, description) and step-by-step instructions
3. **Save it** to `.github/skills/standup-prep/SKILL.md` in your project

That's it — your skill is ready to use.

---

## Try Your New Skill

Once the skill-creator finishes, test it by asking Copilot a natural question:

```
What did I work on yesterday?
```

Copilot will detect the `standup-prep` skill from its description and follow the instructions automatically. If it doesn't trigger, ask the skill-creator to refine the description:

```
Use the skill-creator to improve the description of my standup-prep
skill so it triggers when I ask about daily status or what I did yesterday.
```

---

## More Ideas

Here are a few more skills worth creating with the skill-creator:

- **`debug-ci`** — Diagnose failing GitHub Actions workflows by pulling logs and summarizing errors
- **`pr-review-checklist`** — Run through your team's code review checklist on a pull request diff
- **`format-release-notes`** — Generate release notes from merged PRs since the last tag

For each one, just describe what you want in plain English and let the skill-creator handle the rest.

{: .note }
> Skills created at the project level (`.github/skills/`) travel with the repo — when a colleague clones it, they automatically get your team's skills.

---

{: .tip }
> **🎯 Try it yourself:** Use the skill-creator to build a `standup-prep` skill, then test it by asking Copilot: *"What did I work on yesterday?"*

---

[← Previous: Install Your First Skill]({{ site.baseurl }}/docs/04-first-skill){: .btn .mr-2 }
[Next: Voice Prompting with Handy →]({{ site.baseurl }}/docs/06-voice-prompting){: .btn .btn-primary }
