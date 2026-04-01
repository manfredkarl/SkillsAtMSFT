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

MCP servers are what transform Copilot CLI from a code assistant into a full enterprise productivity tool. In this module you'll connect Copilot to your Microsoft 365 data, CRM system, and Power BI reports - giving it real-time context about your work, customers, and analytics.

---

## What is MCP?

The [Model Context Protocol](https://modelcontextprotocol.io/) (MCP) is an open standard that lets AI assistants connect to external data sources and tools. Think of MCP servers as **plugins** that give Copilot new abilities - each server exposes a set of tools that Copilot can call on your behalf.

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

Once WorkIQ is connected, the real magic begins. These prompts show what's possible when Copilot has full access to your M365 data - emails, Teams, calendar, and files working together.

**"What did I miss?"**

```
Pull everything from my emails, Teams messages, and calendar from the 
last 2 business days. Identify the top 5 things that need my attention - 
action items assigned to me, decisions waiting on me, meetings I need to 
prep for, and anything urgent.
```

Copilot triages across all your communication channels at once - no more switching between Outlook, Teams, and Calendar to piece together what happened while you were out.

**Account 360**

```
Pick my most-mentioned customer from the last week of emails and Teams 
messages. Then do a full 360: pull every internal thread, email, and 
meeting note about them, research their latest news, and generate a 
briefing with our engagement history and recommended next steps.
```

One prompt replaces 30 minutes of manual research. You get a complete customer briefing - engagement history, open threads, and actionable next steps - ready to share with your team.

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

The MSX CRM server connects Copilot to Dynamics 365 - giving it access to accounts, opportunities, activities, and pipeline data from Microsoft Sales Experience.

Once configured, Copilot can query and update your CRM data with prompts like:

- *"Show me the top 5 opportunities closing this quarter"*
- *"What's the latest activity on the Contoso account?"*
- *"Update the revenue estimate for opportunity OPP-1234 to $500K"*

```json
{
  "servers": {
    "msx-crm": {
      "type": "stdio",
      "command": "node",
      "args": ["mcp/msx/src/index.js"],
      "env": {
        "MSX_CRM_URL": "https://microsoftsales.crm.dynamics.com",
        "MSX_TENANT_ID": "${input:tenant_id}"
      }
    }
  }
}
```

---

## Power BI (Remote MCP)

Query your Power BI semantic models using plain English. Ask questions about revenue, trends, KPIs - Copilot translates your question into DAX and returns the answer.

- *"What was total revenue by region last quarter?"*
- *"Show me the trend of customer churn over the past 12 months"*

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

{: .note }
> You need access to at least one Power BI workspace and semantic model. Authenticates via your Microsoft Entra credentials.

---

## Further Helpful MSFT-Internal MCP Servers

These Agent365 servers give Copilot direct access to Microsoft 365 services via Microsoft Graph. They work for all Microsoft employees.

{: .note }
> **WorkIQ vs Agent365 - what's the difference?**
>
> **WorkIQ** is great for **searching and reading** across all your M365 data in one go - emails, Teams, calendar, SharePoint. If you just need to find or summarize information, WorkIQ is all you need.
>
> **Agent365** servers add **direct actions** on individual services - sending emails, posting in Teams, creating calendar events, editing Word docs. If you want Copilot to *do things* (not just read), add the Agent365 servers you need.

{: .tip }
> **Setup:** Add any of these to `.vscode/mcp.json` in your repo root. The `tenant_id` input will prompt you on first use - use your corporate Microsoft Entra tenant GUID.

---

### 📧 Agent365 Mail

Send, receive, and search emails directly from Copilot. Great for drafting responses, summarizing threads, or finding attachments without leaving your terminal.

- *"Draft a reply to the latest email from Sarah about the Q2 budget"*
- *"Find all emails with attachments from last week"*

```json
{
  "servers": {
    "agent365-mail": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/${input:tenant_id}/servers/mcp_MailTools"
    }
  }
}
```

---

### 💬 Agent365 Teams

Read and send Teams messages. Useful for catching up on channels you missed or posting updates without context-switching.

- *"Summarize what was discussed in the #project-alpha channel today"*
- *"Post a status update to my team's general channel"*

```json
{
  "servers": {
    "agent365-teamsserver": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/${input:tenant_id}/servers/mcp_TeamsServer"
    }
  }
}
```

---

### 📅 Agent365 Calendar

Manage your calendar - check availability, create meetings, and review upcoming events. Especially powerful combined with WorkIQ for automated meeting prep.

- *"What's my schedule for tomorrow?"*
- *"Find a 30-minute slot with Jessica and Tom next week"*

```json
{
  "servers": {
    "agent365-calendartools": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/${input:tenant_id}/servers/mcp_CalendarTools"
    }
  }
}
```

---

### 📄 Agent365 Word

Read and work with Word documents stored in OneDrive or SharePoint. Let Copilot extract key information from long documents so you don't have to read them yourself.

- *"Summarize the executive summary from the Q1 strategy doc"*
- *"Extract the action items from the meeting minutes document"*

```json
{
  "servers": {
    "agent365-wordserver": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/${input:tenant_id}/servers/mcp_WordServer"
    }
  }
}
```

---

### 📂 Agent365 SharePoint

Access files and content from SharePoint and OneDrive - search across your org's shared resources, find documents, and browse folder structures.

- *"Find the latest version of the partner onboarding deck on SharePoint"*
- *"List all files in our team's shared project folder"*

```json
{
  "servers": {
    "agent365-sharepoint": {
      "type": "http",
      "url": "https://agent365.svc.cloud.microsoft/agents/tenants/${input:tenant_id}/servers/mcp_ODSPRemoteServer"
    }
  }
}
```

---

[← Previous: Install & Authenticate]({{ site.baseurl }}/docs/01-install-authenticate){: .btn .mr-2 }
[Next: Markdown Notebook →]({{ site.baseurl }}/docs/03-obsidian-integration){: .btn .btn-primary }

