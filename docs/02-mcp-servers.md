---
title: 2. Connect MCP Servers
nav_order: 2
---

# Connect to Data via MCP Servers
{: .fs-8 }

Enhance Copilot CLI by connecting to Model Context Protocol (MCP) servers that expose enterprise data sources.
{: .fs-5 .fw-300 }

---

## What is MCP?

The [Model Context Protocol](https://modelcontextprotocol.io/) (MCP) is an open standard that lets AI assistants connect to external data sources and tools. By adding MCP servers, Copilot CLI gains access to your emails, CRM data, Power BI reports, and more.

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

Add WorkIQ to your MCP server settings (e.g., `~/.copilot/mcp.json` or VS Code `settings.json`):

```json
{
  "servers": {
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

---

## MSX CRM (Dynamics 365)

The `msx-copilot-mcp` server enables Copilot to read and write Dynamics 365 (CRM) data.

### Setup

1. Clone or obtain the MSX MCP server
2. Install dependencies: `npm install`
3. Start the server: `npm start`

### Configure MCP

Add to your `~/.copilot/mcp.json`:

```json
{
  "servers": {
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

---

## Power BI (Remote MCP)

Add the remote Power BI server for natural-language queries against your semantic models:

```json
{
  "servers": {
    "powerbi-remote": {
      "type": "http",
      "url": "https://api.fabric.microsoft.com/v1/mcp/powerbi"
    }
  }
}
```

This allows Copilot to query Power BI datasets using plain English.

---

## Custom MCP Tools

If you have custom scripts or APIs, define them similarly under MCP servers. For example:

```json
{
  "servers": {
    "my-custom-tool": {
      "type": "stdio",
      "command": "node",
      "args": ["/path/to/my-tool/index.js"]
    }
  }
}
```

---

## Testing MCP Connections

Use `/mcp status` in Copilot CLI (or check the MCP panel in VS Code) to confirm your servers are connected and healthy.

{: .tip }
> If a server shows as disconnected, check that the command path is correct and any required environment variables are set.

---

[← Previous: Install & Authenticate]({{ site.baseurl }}/docs/01-install-authenticate){: .btn .mr-2 }
[Next: Integrate Obsidian →]({{ site.baseurl }}/docs/03-obsidian-integration){: .btn .btn-primary }
