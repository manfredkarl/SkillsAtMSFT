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

### Troubleshooting Installation

{: .warning }
> **Common issues:**
> - **Permission errors on macOS/Linux?** Avoid `sudo npm install -g`. Instead, [fix your npm permissions](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) or use `nvm`.
> - **`copilot` command not found?** Make sure your global npm `bin` directory is in your `PATH`. Run `npm config get prefix` to find it.
> - **Behind a corporate proxy?** Set `HTTP_PROXY` and `HTTPS_PROXY` environment variables before installing.

---

## Authenticate

In your terminal, launch Copilot and follow the interactive prompts to log in with your GitHub account:

```bash
copilot
```

The CLI will open a browser window for GitHub OAuth authentication. After you approve:

1. **Device code flow** — Copy the code shown in your terminal, paste it in the browser, and authorize the app.
2. **Repository trust** — Copilot will ask you to confirm that you trust the current workspace. Approve it to allow file access.
3. **Success** — You'll see a welcome message in the terminal confirming you're logged in.

{: .note }
> **Alternative: Token-based auth.** If browser-based login isn't possible (e.g., headless servers), set the `GH_TOKEN` or `GITHUB_TOKEN` environment variable with a [fine-grained personal access token](https://github.com/settings/personal-access-tokens/new) that has the **Copilot Requests** permission:
> ```bash
> export GH_TOKEN=github_pat_your_token_here         # macOS/Linux
> $env:GH_TOKEN = "github_pat_your_token_here"        # PowerShell
> ```

---

## Allow Autonomy (`--allow-all`)

Start Copilot CLI with full permissions using the `--allow-all` flag:

```bash
copilot --allow-all
```

This is equivalent to `--allow-all-tools --allow-all-paths --allow-all-urls`, letting Copilot automatically use tools, access all file paths, and reach any URL without further confirmation. In this workshop we recommend using `--allow-all` so you can focus on learning rather than approving each action.

{: .note }
> The legacy `--yolo` flag still works as an alias for `--allow-all`.

{: .warning }
> **Security note:** Granting `--allow-all` gives Copilot CLI permission to modify any files or run any command it deems necessary.
> Use `--allow-all` only when you trust the assistant and the workspace content.
> If you prefer more safety, omit `--allow-all` and Copilot will prompt you for each tool or path access.

---

## Verify Your Install

After starting Copilot, confirm the CLI is working:

```bash
copilot --version
```

You should see the version number printed (e.g., `1.x.x`). Then start an interactive session to confirm authentication works end-to-end:

```bash
copilot
```

Type a simple prompt like `"What directory am I in?"` — if Copilot responds with your current path, everything is working correctly.

> **References:** [Installing Copilot CLI](https://docs.github.com/copilot/how-tos/set-up/install-copilot-cli) · [npm: @github/copilot](https://www.npmjs.com/package/@github/copilot) · [GitHub Copilot CLI repo](https://github.com/github/copilot-cli)

---

{: .tip }
> **🎯 Try it yourself:** Start Copilot CLI and ask it to list all files in your current directory. Then ask it to explain what one of those files does. This confirms that both authentication and tool access are working correctly.

---

[Next: Connect MCP Servers →]({{ site.baseurl }}/docs/02-mcp-servers){: .btn .btn-primary }
