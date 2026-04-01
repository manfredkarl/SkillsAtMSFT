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

### Quick Install

The quickest way to add WorkIQ is to just ask Copilot:

> *"Install WorkIQ so I can access my emails and calendar"*

Copilot will handle the setup for you. Alternatively, you can install it manually:

### Install the Plugin

Run these commands in Copilot CLI:

```
/plugin marketplace add github/copilot-plugins
/plugin install workiq@copilot-plugins
```

### Configure MCP (optional)

The plugin install above already sets up the connection. If you want to configure WorkIQ manually (e.g., for VS Code), add it to your MCP server settings (`~/.copilot/mcp-config.json` or `.vscode/mcp.json`):

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

### Power Prompts

Once WorkIQ is connected, the real magic begins. These prompts show what's possible when Copilot has full access to your M365 data — emails, Teams, calendar, and files working together.

**"What did I miss?"**

```
Pull everything from my emails, Teams messages, and calendar from the 
last 2 business days. Identify the top 5 things that need my attention — 
action items assigned to me, decisions waiting on me, meetings I need to 
prep for, and anything urgent.
```

Copilot triages across all your communication channels at once — no more switching between Outlook, Teams, and Calendar to piece together what happened while you were out.

**Account 360**

```
Pick my most-mentioned customer from the last week of emails and Teams 
messages. Then do a full 360: pull every internal thread, email, and 
meeting note about them, research their latest news, and generate a 
briefing with our engagement history and recommended next steps.
```

One prompt replaces 30 minutes of manual research. You get a complete customer briefing — engagement history, open threads, and actionable next steps — ready to share with your team.

**Meeting prep on autopilot**

```
Look at my calendar for the next 2 business days. For each external 
customer meeting, pull the last 5 email and Teams exchanges with that 
customer, summarize what we've discussed recently, identify any open 
action items, and generate a prep doc with talking points for each meeting.
```

Walk into every customer meeting fully briefed. Copilot cross-references your calendar with your communication history and builds personalized prep docs automatically.

---

## MSX CRM (Dynamics 365)

The MSX CRM server connects Copilot to Dynamics 365 — giving it access to accounts, opportunities, activities, and pipeline data from Microsoft Sales Experience.

Once configured, Copilot can query and update your CRM data with prompts like:

- *"Show me the top 5 opportunities closing this quarter"*
- *"What's the latest activity on the Contoso account?"*
- *"Update the revenue estimate for opportunity OPP-1234 to $500K"*

---

## Full MCP Configuration

Below is a complete `.vscode/mcp.json` you can drop into your repo root. It includes all the servers we've covered plus additional Agent365 connectors for Mail, Teams, Calendar, Word, and SharePoint.

```json
{
  "servers": {
    "workiq": {
      "command": "npx",
      "args": ["-y", "@microsoft/workiq", "mcp"],
      "type": "stdio"
    },
    "msx-crm": {
      "type": "stdio",
      "command": "node",
      "args": ["mcp/msx/src/index.js"],
      "env": {
        "MSX_CRM_URL": "https://microsoftsales.crm.dynamics.com",
        "MSX_TENANT_ID": "${input:tenant_id}"
      }
    },
    "oil": {
      "type": "stdio",
      "command": "node",
      "args": ["scripts/oil-start.js"]
    },
    "powerbi-remote": {
      "type": "http",
      "url": "https://api.fabric.microsoft.com/v1/mcp/powerbi"
    },
    "agent365-mail": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/${input:tenant_id}/servers/mcp_MailTools"
    },
    "agent365-teamsserver": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/${input:tenant_id}/servers/mcp_TeamsServer"
    },
    "agent365-calendartools": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/${input:tenant_id}/servers/mcp_CalendarTools"
    },
    "agent365-wordserver": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/${input:tenant_id}/servers/mcp_WordServer"
    },
    "agent365-sharepoint": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/${input:tenant_id}/servers/mcp_ODSPRemoteServer"
    }
  },
  "inputs": [
    {
      "id": "tenant_id",
      "type": "promptString",
      "description": "Microsoft Entra tenant ID (GUID)"
    }
  ]
}
```

### Servers Included

| Server | What it does |
|:-------|:-------------|
| **WorkIQ** | M365 content search (meetings, chats, email, SharePoint) |
| **MSX-CRM** | Dynamics 365 CRM read/write operations |
| **OIL** | Obsidian Intelligence Layer (local knowledge vault) |
| **Power BI Remote** | Fabric/Power BI semantic model queries |
| **Agent365 Mail** | Send/receive email via Graph |
| **Agent365 Teams** | Teams messaging and chat |
| **Agent365 Calendar** | Calendar and meeting management |
| **Agent365 Word** | Word document operations |
| **Agent365 SharePoint** | SharePoint/OneDrive file operations |

{: .note }
> **Setup:** Place this as `.vscode/mcp.json` in your repo root. The `tenant_id` input will prompt you on first use — use your corporate Microsoft Entra tenant GUID.

---

[← Previous: Install & Authenticate]({{ site.baseurl }}/docs/01-install-authenticate){: .btn .mr-2 }
[Next: Integrate Obsidian →]({{ site.baseurl }}/docs/03-obsidian-integration){: .btn .btn-primary }
