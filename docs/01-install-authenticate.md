---
title: 1. Install & Authenticate
nav_order: 1
---

# Install & Authenticate Copilot CLI
{: .fs-8 }

Get Copilot CLI installed and authenticated in under 5 minutes.
{: .fs-5 .fw-300 }

⏱️ **Estimated time: 5–10 minutes**

In this module you'll install the Copilot CLI, authenticate with your GitHub account, and verify everything works. This is the foundation for every module that follows - once you're authenticated, all the advanced features (MCP servers, skills, voice prompting) become available.

---

## Prerequisites

Before you begin, make sure you have the following ready:

- **Node.js 22+** - [Download here](https://nodejs.org/). Run `node --version` to check your current version.
- **GitHub account** with a Copilot subscription (Pro, Pro+, Business, or Enterprise)
- **PowerShell v6+** (Windows) or any modern terminal (macOS/Linux)

{: .note }
> **Not sure if you have Copilot access?** Visit [github.com/settings/copilot](https://github.com/settings/copilot) to check your subscription status. If your organization manages your license, ask your admin to confirm your seat assignment.

---

## Link Your GitHub Account to Microsoft

To use Copilot CLI under the Microsoft enterprise license, your GitHub account must be linked to your Microsoft identity.

1. **Need a GitHub account?** Create one at [github.com/signup](https://github.com/signup).
2. **Link your @microsoft.com identity** - Follow Microsoft's internal instructions to associate your GitHub account with your corporate identity. This grants access to Copilot under the enterprise agreement.
3. **Already linked?** Skip this step and move on to installation.

{: .note }
> If you're unsure whether your account is linked, check [github.com/settings/copilot](https://github.com/settings/copilot) - you should see your enterprise subscription listed.

---

## Install the CLI

### Windows

{: .tip }
> **Before you install, make sure you have these:**
> - ✅ **Windows Terminal** - [Download here](https://aka.ms/terminal) (modern tabbed terminal, highly recommended)
> - ✅ **PowerShell 7** - *Not* the built-in Windows PowerShell 5.1. Install: `winget install Microsoft.PowerShell`. Verify: `$PSVersionTable.PSVersion` should show 7.x+
> - ✅ **Git** - [git-scm.com](https://git-scm.com) if not already installed
> - ✅ **Node.js 22+** - [nodejs.org](https://nodejs.org/) (LTS version)

Open **Windows Terminal** (or PowerShell 7) and install using **npm** (recommended) or **winget**:

```powershell
npm install -g @github/copilot
```

```powershell
winget install GitHub.Copilot
```

{: .tip }
> If you have `ignore-scripts=true` in your `~/.npmrc`, use:
> ```powershell
> $env:npm_config_ignore_scripts = "false"; npm install -g @github/copilot
> ```

### macOS/Linux

Open your terminal and install using **npm** (recommended) or **Homebrew**:

```bash
npm install -g @github/copilot
```

```bash
brew install copilot-cli
```

{: .tip }
> If you have `ignore-scripts=true` in your `~/.npmrc`, use:
> ```bash
> npm_config_ignore_scripts=false npm install -g @github/copilot
> ```

### Troubleshooting Installation

{: .warning }
> **Common issues:**
> - **`copilot` command not found?** Make sure your global npm `bin` directory is in your `PATH`. Run `npm config get prefix` to find it.
> - **Permission errors on macOS/Linux?** Avoid `sudo npm install -g`. Instead, [fix your npm permissions](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) or use `nvm`.
> - **Behind a corporate proxy?** Set `HTTP_PROXY` and `HTTPS_PROXY` environment variables before installing.

---

## Authenticate

Run Copilot in your terminal:

```bash
copilot
```

On first launch, the CLI will prompt you to log in with your GitHub account:

1. **Device code flow** - The CLI displays a one-time code and opens your browser to [github.com/login/device](https://github.com/login/device). Enter the code and authorize the app.
2. **Workspace trust** - Copilot will ask you to confirm that you trust the current workspace. Approve to allow file access.
3. **Ready to go** - You'll see a welcome message confirming you're logged in. You can start prompting immediately.

---

## Allow Autonomy (`--yolo`)

Start Copilot CLI with full permissions using the `--yolo` flag:

```bash
copilot --yolo
```

This is equivalent to `--allow-all-tools --allow-all-paths --allow-all-urls`, letting Copilot automatically use tools, access all file paths, and reach any URL without further confirmation. In this workshop we recommend using `--yolo` so you can focus on learning rather than approving each action.

{: .note }
> The `--allow-all` flag also works as an alias for `--yolo`.

{: .warning }
> **Security note:** Granting `--yolo` gives Copilot CLI permission to modify any files or run any command it deems necessary.
> Use `--yolo` only when you trust the assistant and the workspace content.
> If you prefer more safety, omit `--yolo` and Copilot will prompt you for each tool or path access.

---

## Select Your Model

Once inside Copilot CLI, choose the model that powers your interactions:

```
/model
```

This shows all available models. We recommend selecting **Claude Opus 4.6** for the most capable reasoning and highest-quality output. Other options include Claude Sonnet (faster, lighter) and GPT-5 variants.

{: .tip }
> Model choice makes a real difference in output quality - especially for complex analysis, writing, and multi-step tasks. Start with Opus and adjust if you need faster responses.

---

## Useful Commands

Copilot CLI saves your conversation history as **sessions** and has handy slash commands you can use anytime:

| Command | What it does |
|:--------|:-------------|
| `/resume` | Browse and switch between recent sessions |
| `/rename` | Give the current session a meaningful name |
| `/session` | View current session info |
| `/compact` | Summarize conversation to free up context window |
| `/share` | Export session to markdown or GitHub Gist |
| `/clear` | Abandon session and start fresh |
| `/model` | Switch AI model |
| `/skills` | List installed skills |
| `/mcp` | Manage MCP server connections |
| `/help` | Show all available commands |

---

## Tips for Getting the Most Out of It

- **Use `@` to reference files** - Type `@` followed by a filename to include its contents in your prompt. Great for feeding data, CSVs, transcripts, or reusable prompts.
- **Ask for file output** - End any prompt with *"save this as a well-formatted HTML file"* and you'll get a polished document in your working folder. Open it in your browser.
- **Iterate instantly** - Don't like the output? Just say *"make this better"* or *"add a chart"* or *"make this more executive-ready."* Copilot refines in place.
- **Build a prompt library** - Ask Copilot to *"create a reusable prompt file that does [X] and save it as a markdown file."* Then reference it anytime with `@filename.md`.

---

{: .tip }
> **🎯 Try it yourself:** Start Copilot CLI and ask it to list all files in your current directory. Then ask it to explain what one of those files does. This confirms that both authentication and tool access are working correctly.

---

[Next: Connect MCP Servers →]({{ site.baseurl }}/docs/02-mcp-servers){: .btn .btn-primary }

