---
title: 1. Install & Authenticate
nav_order: 1
---

# Install & Authenticate Copilot CLI
{: .fs-8 }

Get Copilot CLI installed and authenticated in under 5 minutes.
{: .fs-5 .fw-300 }

⏱️ **Estimated time: 5–10 minutes**

In this module you'll install the Copilot CLI, authenticate with your GitHub account, and verify everything works. This is the foundation for every module that follows — once you're authenticated, all the advanced features (MCP servers, skills, voice prompting) become available.

---

## Prerequisites

Before you begin, make sure you have the following ready:

- **Node.js 22+** — [Download here](https://nodejs.org/). Run `node --version` to check your current version.
- **GitHub account** with a Copilot subscription (Pro, Pro+, Business, or Enterprise)
- **PowerShell v6+** (Windows) or any modern terminal (macOS/Linux)

{: .note }
> **Not sure if you have Copilot access?** Visit [github.com/settings/copilot](https://github.com/settings/copilot) to check your subscription status. If your organization manages your license, ask your admin to confirm your seat assignment.

---

## Install the CLI

### Windows

Install using **npm** (recommended) or **winget**:

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

Install using **npm** (recommended) or **Homebrew**:

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

1. **Device code flow** — The CLI displays a one-time code and opens your browser to [github.com/login/device](https://github.com/login/device). Enter the code and authorize the app.
2. **Workspace trust** — Copilot will ask you to confirm that you trust the current workspace. Approve to allow file access.
3. **Ready to go** — You'll see a welcome message confirming you're logged in. You can start prompting immediately.

{: .note }
> **Alternative: Token-based auth.** If browser-based login isn't possible (e.g., headless servers), set the `COPILOT_GITHUB_TOKEN`, `GH_TOKEN`, or `GITHUB_TOKEN` environment variable with a [fine-grained personal access token](https://github.com/settings/personal-access-tokens/new) that has the **Copilot Requests** permission:
> ```bash
> export GH_TOKEN=github_pat_your_token_here         # macOS/Linux
> $env:GH_TOKEN = "github_pat_your_token_here"        # PowerShell
> ```

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

{: .tip }
> **🎯 Try it yourself:** Start Copilot CLI and ask it to list all files in your current directory. Then ask it to explain what one of those files does. This confirms that both authentication and tool access are working correctly.

---

[Next: Connect MCP Servers →]({{ site.baseurl }}/docs/02-mcp-servers){: .btn .btn-primary }
