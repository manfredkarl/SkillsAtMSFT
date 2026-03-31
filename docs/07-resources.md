---
title: 7. Resources & Skill Repos
nav_order: 7
---

# Resources & Skill Repos
{: .fs-8 }

Curated skill repositories and resources to supercharge your Copilot CLI setup.
{: .fs-5 .fw-300 }

---

## Skill Repositories

These are the main sources for pre-built agent skills you can install with `npx skills add`:

### Anthropic Skills

```bash
npx skills add anthropics/skills --list
```

A growing collection of high-quality skills including `skill-creator`, `pptx`, and more. This is the go-to repo for foundational skills.

🔗 [github.com/anthropics/skills](https://github.com/anthropics/skills/tree/main)

---

### Vercel Skills (skills.sh)

```bash
npx skills add vercel-labs/agent-skills --list
```

The open agent skills marketplace. Browse, search, and install community-contributed skills. Includes skills for frontend design, deployment, and more.

🔗 [skills.sh](https://skills.sh/)

---

### Microsoft: Awesome Copilot Skills

A curated list of skills specifically designed for GitHub Copilot workflows — from code review to CI/CD debugging.

🔗 [github.com/github/awesome-copilot/skills](https://github.com/github/awesome-copilot/tree/main/skills/)

---

### Microsoft Skills

Microsoft's official skills repository with enterprise-focused skills for Microsoft technologies and workflows.

🔗 [github.com/microsoft/skills](https://github.com/microsoft/skills)

---

## Quick Install Cheatsheet

```bash
# Browse what's available
npx skills add anthropics/skills --list
npx skills add vercel-labs/agent-skills --list

# Install a specific skill (project-level)
npx skills add anthropics/skills --skill skill-creator

# Install globally (available in all projects)
npx skills add anthropics/skills --skill pptx -g

# Search for skills by keyword
npx skills find "code review"
```

{: .tip }
> Remember: use `-g` for skills you want everywhere (personal productivity), and default (no flag) for project-specific skills that should travel with the repo.

---

[← Previous: Voice Prompting]({{ site.baseurl }}/docs/06-voice-prompting){: .btn .mr-2 }
[Back to Home]({{ site.baseurl }}/){: .btn .btn-primary }
