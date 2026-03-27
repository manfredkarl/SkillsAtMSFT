---
title: 2. Connect MCP Servers
nav_order: 2
---

# Connect to Data via MCP Servers
{: .fs-8 }

Enhance Copilot CLI by connecting to Model Context Protocol (MCP) servers that expose enterprise data sources.
{: .fs-5 .fw-300 }

---

⏱️ **Estimated time: 10–15 minutes**

MCP servers are what transform Copilot CLI from a code assistant into a full enterprise productivity tool. In this module you'll connect Copilot to your Microsoft 365 data, CRM system, and Power BI reports — giving it real-time context about your work, customers, and analytics.

---

## What is MCP?

The [Model Context Protocol](https://modelcontextprotocol.io/) (MCP) is an open standard that lets AI assistants connect to external data sources and tools. Think of MCP servers as **plugins** that give Copilot new abilities — each server exposes a set of tools that Copilot can call on your behalf.

There are two types of MCP connections:

| Type | How it works | Example |
|:-----|:-------------|:--------|
| **stdio** | Copilot launches a local process and communicates via stdin/stdout | WorkIQ, MSX CRM |
| **http** | Copilot connects to a remote HTTP endpoint | Power BI |

All MCP configuration lives in `~/.copilot/mcp-config.json` (for Copilot CLI) or your VS Code `.vscode/mcp.json`.

---

## WorkIQ (Microsoft 365 Data)

WorkIQ provides access to your emails, calendar, Teams chats, and files from Microsoft 365.

### Install the Plugin

Run these commands in Copilot CLI:

```
/plugin marketplace add github/copilot-plugins
/plugin install workiq@copilot-plugins
```

### Configure MCP

Add WorkIQ to your MCP server settings (e.g., `~/.copilot/mcp-config.json` or VS Code `.vscode/mcp.json`):

```json
{
  "mcpServers": {
    "workiq": {
      "command": "npx",
      "args": ["-y", "@microsoft/workiq", "mcp"],
      "type": "stdio",
      "tools": ["*"]
    }
  }
}
```

Then accept the license agreement once:

```
workiq accept-eula
```

### Use WorkIQ

After configuration, Copilot can query your Microsoft 365 context. Try prompts like:

- *"What did my manager say about the Q1 roadmap?"*
- *"Summarize my unread emails from today"*
- *"What meetings do I have this week?"*
- *"Find the document that was shared in last Friday's team meeting"*

{: .note }
> **First-time auth:** The first time you use WorkIQ, it will trigger a Microsoft Entra login flow in your browser. Sign in with your corporate account and grant the requested permissions. This only happens once.

> **References:** [WorkIQ CLI overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/workiq-overview) · [WorkIQ MCP README](https://github.com/microsoft/work-iq-mcp)

---

## MSX CRM (Dynamics 365)

The `msx-copilot-mcp` server enables Copilot to read and write Dynamics 365 (CRM) data.

### Setup

1. Clone or obtain the MSX MCP server repository
2. Install dependencies: `npm install`
3. Start the server: `npm start`
4. Verify it starts without errors — you should see a "listening" message

### Configure MCP

Add to your `~/.copilot/mcp-config.json`:

```json
{
  "mcpServers": {
    "msx-crm": {
      "type": "stdio",
      "command": "node",
      "args": ["/absolute/path/to/msx-copilot-mcp/mcp-server/src/index.js"],
      "env": {
        "MSX_CRM_URL": "https://microsoftsales.crm.dynamics.com",
        "MSX_TENANT_ID": "<your-tenant-id>"
      }
    }
  }
}
```

{: .note }
> Replace the path and tenant ID with your own values. Changes to CRM data will require human approval.

{: .warning }
> **Windows users:** Use double backslashes in JSON paths (e.g., `C:\\Users\\you\\msx-copilot-mcp\\...`) or use forward slashes instead.

### Example CRM Queries

Once connected, try prompts like:

- *"Show me the top 5 opportunities closing this quarter"*
- *"What's the latest activity on the Contoso account?"*
- *"Update the revenue estimate for opportunity OPP-1234 to $500K"*

---

## Power BI (Remote MCP)

Add the remote Power BI server for natural-language queries against your semantic models:

```json
{
  "mcpServers": {
    "powerbi-remote": {
      "type": "http",
      "url": "https://api.fabric.microsoft.com/v1/mcp/powerbi"
    }
  }
}
```

This allows Copilot to query Power BI datasets using plain English. For example:

- *"What was total revenue by region last quarter?"*
- *"Show me the trend of customer churn over the past 12 months"*

{: .note }
> You must have access to at least one Power BI workspace and semantic model. The remote MCP server authenticates using your Microsoft Entra credentials.

> **References:** [Remote Power BI MCP server](https://learn.microsoft.com/en-us/power-bi/developer/mcp/remote-mcp-server-get-started)

---

## Custom MCP Tools

If you have custom scripts or APIs, define them similarly under MCP servers. For example:

```json
{
  "mcpServers": {
    "my-custom-tool": {
      "type": "stdio",
      "command": "node",
      "args": ["/path/to/my-tool/index.js"]
    }
  }
}
```

Custom tools can expose any functionality — database queries, internal APIs, file transformations, or webhook triggers. Each tool you define becomes callable by Copilot when relevant to a user's prompt.

---

## Testing MCP Connections

After adding servers, always verify they're connected. Use `/mcp status` in Copilot CLI (or check the MCP panel in VS Code) to confirm your servers are connected and healthy.

You should see each server listed with a **connected** status and the number of available tools.

### Troubleshooting

{: .tip }
> **Server shows "disconnected"?** Check these common causes:
> - **Wrong path:** Ensure the `command` and `args` point to the correct executable. Use absolute paths.
> - **Missing dependencies:** Run `npm install` in the server directory if it's a Node.js project.
> - **Environment variables:** Make sure all required `env` values are set (e.g., tenant IDs, URLs).
> - **Port conflicts:** For HTTP servers, verify the port isn't already in use.
> - **Reload config:** After editing `mcp-config.json`, restart Copilot CLI or run `/mcp reload` to pick up changes.

---

{: .tip }
> **🎯 Try it yourself:** Configure the WorkIQ MCP server and ask Copilot *"What meetings do I have today?"*. If you don't have WorkIQ access, try adding the Power BI remote server and query one of your datasets using natural language.

---

[← Previous: Install & Authenticate]({{ site.baseurl }}/docs/01-install-authenticate){: .btn .mr-2 }
[Next: Integrate Obsidian →]({{ site.baseurl }}/docs/03-obsidian-integration){: .btn .btn-primary }
