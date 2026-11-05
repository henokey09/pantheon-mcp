# Pantheon MCP server

[![AllMCPs](https://allmcps.com/api/badge/pantheon?style=directory)](https://allmcps.com/mcp/pantheon?verify=28b164ca-6460-4bb1-af7e-9d1bd213581c)
[![Listed on MCPpedia](https://mcppedia.com/badge/pantheon-mcp.svg)](https://mcppedia.com/servers/pantheon-mcp)
[![mcptry](https://mcptry.com/badge/ad.pantheon/mcp)](https://mcptry.com/servers/ad.pantheon/mcp)

Remote MCP server for [Pantheon.ad](https://pantheon.ad/en), an ad research tool for coaches, consultants, agencies and B2B teams who advertise on Facebook and Instagram.

Connect it to Claude, Claude Code, Cursor, VS Code or any MCP client and work with your Pantheon account from the chat: search the ads you collected, read the active ads of competitors you analyzed, check this week's Top Ads, and (on the Scale plan) run new analyses and create brand voices and offer briefs.

This repository holds documentation and registry metadata only. The server is hosted by Pantheon; there is nothing to install or run locally.

| | |
|---|---|
| Endpoint | `https://mcp.pantheon.ad/mcp` |
| Transport | Streamable HTTP |
| Auth | OAuth 2.1 with your Pantheon account |
| Registry name | `ad.pantheon/mcp` ([Official MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=ad.pantheon)) |
| Plans | Pro (read tools), Scale (read and action tools). See [pricing](https://pantheon.ad/en/pricing) |

## Install

### Claude Code

```bash
claude mcp add --transport http pantheon https://mcp.pantheon.ad/mcp
```

Then run `/mcp` in Claude Code and sign in with your Pantheon account.

### Claude (web and desktop)

Settings → Connectors → Add custom connector, then paste `https://mcp.pantheon.ad/mcp` and sign in.

### Cursor

Add to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "pantheon": { "url": "https://mcp.pantheon.ad/mcp" }
  }
}
```

### VS Code

Add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "pantheon": { "type": "http", "url": "https://mcp.pantheon.ad/mcp" }
  }
}
```

Any other client: point it at `https://mcp.pantheon.ad/mcp` with Streamable HTTP. The server advertises its OAuth metadata at `/.well-known/oauth-protected-resource/mcp`.

## Tools

### Read tools (Pro and Scale)

| Tool | What it does |
|---|---|
| `list_projects` | Your strategic projects (avatar analyses) and their ids |
| `list_brand_voices` | Your saved brand voices |
| `list_offer_briefs` | Your saved offer briefs |
| `list_analyzed_pages` | Facebook pages you analyzed, with status and ad counts |
| `search_ads_library` | Search the ads collected in your account and this week's Top Ads by brand, niche, sector or copy |
| `get_market_creators_data` | Aggregated stats of the creators and competitors you monitor |
| `get_top_performing_ads` | Longest-running ads of the creators you monitor |
| `get_active_ads_copy` | Body, caption and CTA of their currently active ads |
| `get_saved_ads` | Your swipe file, optionally filtered by competitor |
| `get_strategic_avatar` | Pain matrix, triggers and Socratic hub of a project's target |
| `get_competitor_active_ads` | Active ads of a competitor you analyzed with Competitor Spy |
| `get_creative_analysis` | RMBC analysis (research, mechanism, brief, copy) of an ad, when available |
| `get_job_status` | Status and results of a background job |

### Action tools (Scale)

Each one uses a credit of your plan.

| Tool | What it does |
|---|---|
| `run_competitor_spy` | Collect and analyze the ads of a competitor's Facebook page, with optional weekly monitoring |
| `run_inspiration_search` | Analyze a page outside your niche for ideas |
| `run_brand_campaign_analysis` | Analyze your own brand's Meta campaigns page |
| `run_ad_copilot` | Adapt an ad into 3 copy variants for your avatar, offer brief and brand voice |
| `analyze_ad` | Full analysis of one ad: emotional levers, biases, landing page coherence |
| `run_persuasion_analysis` | Check an ad before launch for present and missing cognitive biases |
| `run_sales_psychology` | Sales psychology report for an avatar and an offer brief |
| `create_brand_voice` | Create a brand voice from a public URL or a text |
| `create_offer_brief` | Create an offer brief from a sales page URL or a text |
| `run_magic_tool` | Summarize, translate or extract contacts and links from a text |

Long jobs run in the background: the tool returns an id, and `get_job_status` returns the result.

## Example prompts

- "List the active ads of the competitors I'm tracking and group them by hook."
- "Search my ads for 'webinar' and show the three that have been running longest."
- "Take ad 123 and adapt it with my 'Coaching offer' brief and my brand voice." (Scale)

## Support

support@pantheon.ad · [pantheon.ad](https://pantheon.ad/en)

The documentation in this repository is released under the MIT license. The Pantheon service is governed by its own terms.

<!-- mcppedia-verify-f5ccb895bfa953601019a26e844cd044 -->
