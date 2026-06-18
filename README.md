<p align="center">
  <a href="https://humanhours.dev">
    <img src="https://humanhours.dev/icon.svg" alt="HumanHours" width="96" height="96" />
  </a>
</p>

<h1 align="center">HumanHours MCP Server</h1>

<p align="center">
  <em>Every agent, measured in human hours.</em><br/>
  <a href="https://humanhours.dev">humanhours.dev</a> ·
  <a href="https://humanhours.dev/docs/mcp">MCP docs</a>
</p>

Track agent ROI and enrich companies straight from any MCP client. HumanHours is a
remote, hosted MCP server: connect once with your HumanHours account and your agents
can log task events, read what they saved, and pull real labour-cost data for any company.

No installation, no API keys to copy around, no local process to run.

## Connect

| | |
|---|---|
| **Endpoint** | `https://mcp.humanhours.dev/mcp` |
| **Transport** | Streamable HTTP |
| **Auth** | OAuth 2.1 (PKCE) — browser login with your HumanHours account, approve workspace access |

Add it to any client that supports remote MCP servers (Claude Desktop, claude.ai,
Cursor, and others). On first use you complete a browser login and approve the scopes
below; the client stores a token, so there are no keys to manage by hand.

### Claude Desktop / claude.ai

Add a remote connector pointing at `https://mcp.humanhours.dev/mcp` and complete the
login when prompted.

### Cursor / other clients

```json
{
  "mcpServers": {
    "humanhours": {
      "url": "https://mcp.humanhours.dev/mcp"
    }
  }
}
```

## Tools

**Logging**
- `track_event` — Record one agent task event and compute the hours and money it saved.

**Reading**
- `get_summary` — Aggregated ROI for a period, with a daily trend.
- `time_saved_report` — Hours saved, grouped by agent, task type, model, client, or time.
- `cost_saved_report` — Money saved, grouped the same ways.
- `leaderboard` — Top agents by a chosen metric.
- `get_usage` — Event usage against the plan's included quota.
- `list_agents` — Agents tracked, with 30-day hours and money saved.
- `list_task_types` — Built-in plus custom task types.

**Enrichment**
- `enrich_company` — Turn a domain into roles, per-hour wages, and an annual labour-cost case.
- `get_company` — Read one enriched company from the library.
- `list_companies` — List the workspace's company library, optionally by tag.
- `bulk_enrich` — Queue a background job for many domains; returns a job id.
- `get_job` — Check the status of a bulk enrichment job.

## Scopes

| Scope | Grants |
|---|---|
| `track:write` | Log task events |
| `read:reports` | Read ROI summaries, reports, leaderboards, usage |
| `enrich:write` | Enrich companies and read the company library |

## Docs

Full connection guide, scopes, and tool reference: https://humanhours.dev/docs/mcp

## About

HumanHours is the ROI meter for AI agents: it measures the hours and money your agents
save, and enriches companies with real wage data so every saving is grounded in what the
work actually costs. Learn more at https://humanhours.dev.
