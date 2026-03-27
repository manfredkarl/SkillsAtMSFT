---
title: 1. Install & Authenticate
nav_order: 1
---

# Install & Authenticate Copilot CLI
{: .fs-8 }

Get Copilot CLI installed and authenticated in under 5 minutes.
{: .fs-5 .fw-300 }

---

## Prerequisites

- **Node.js 22+** — [Download here](https://nodejs.org/)
- **GitHub account** with a Copilot subscription (Pro, Pro+, Business, or Enterprise)
- **PowerShell v6+** (Windows) or any modern terminal (macOS/Linux)

---

## Install the CLI

Choose your preferred package manager:

### npm (cross-platform — recommended)

```bash
npm install -g @github/copilot
```

### Homebrew (macOS/Linux)

```bash
brew install copilot-cli
```

### winget (Windows)

```bash
winget install GitHub.Copilot
```

{: .tip }
> If you have `ignore-scripts=true` in your `~/.npmrc`, use:
> ```bash
> npm_config_ignore_scripts=false npm install -g @github/copilot
> ```

---

## Authenticate

In your terminal, launch Copilot and follow the prompts to log in with your GitHub account:

```bash
copilot
```

After login, Copilot will ask to confirm repository trust — approve it. Alternatively, set the `COPILOT_GITHUB_TOKEN` environment variable with a personal access token.

---

## Allow Autonomy (`--yolo`)

Start Copilot CLI with full permissions using the `--yolo` flag:

```bash
copilot --yolo
```

This lets Copilot automatically use tools and access all file paths without further confirmation.

{: .warning }
> **Security note:** Granting `--yolo` gives Copilot CLI permission to modify any files or run any command it deems necessary.
> Use `--yolo` only when you trust the assistant and the workspace content.
> If you prefer more safety, omit `--yolo` and Copilot will prompt you for each tool or path access.

---

## Verify Your Install

After starting Copilot, confirm the CLI is working:

```bash
copilot --version
```

You should see the version number printed. You're ready to move on!

---

[Next: Connect MCP Servers →]({{ site.baseurl }}/docs/02-mcp-servers){: .btn .btn-primary }
