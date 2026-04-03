# google-trends-mcp

[![Google Trends](https://img.shields.io/badge/Google%20Trends-4285F4?style=flat-square)](https://trendsmcp.ai/google-trends)
[![MCP](https://img.shields.io/badge/MCP-compatible-blue?style=flat-square)](https://modelcontextprotocol.io)
[![Works with Claude](https://img.shields.io/badge/Claude-supported-orange?style=flat-square)](https://trendsmcp.ai/mcp-server-for-claude)
[![Works with Cursor](https://img.shields.io/badge/Cursor-supported-purple?style=flat-square)](https://trendsmcp.ai/mcp-server-for-cursor)

> **Google Trends data for AI assistants**
> Ask your AI what is trending on Google right now. Get breakout keywords, rising topics, and 5 years of normalized search interest data - without writing a single line of scraping code.

**Full docs and live demo:** [https://trendsmcp.ai/google-trends](https://trendsmcp.ai/google-trends)

Part of **[Trends MCP](https://trendsmcp.ai)** -- the MCP server for live trend data across 12+ sources.
See the main repo: [https://github.com/trendsmcp/trends-mcp](https://github.com/trendsmcp/trends-mcp)

---

## Get started in 2 steps

**Step 1:** Get your free API key at **[trendsmcp.ai](https://trendsmcp.ai)**
100 requests/day, no credit card required.

**Step 2:** Add to your AI client (replace `YOUR_API_KEY`):

[**+ Add to Cursor (one click)**](cursor://anysphere.cursor-deeplink/mcp/install?name=trends-mcp&config=eyJ1cmwiOiAiaHR0cHM6Ly9hcGkudHJlbmRzbWNwLmFpL21jcCIsICJ0cmFuc3BvcnQiOiAiaHR0cCJ9)

**Cursor / Windsurf / Cline** &nbsp; (`~/.cursor/mcp.json` or equivalent)
```json
{
  "mcpServers": {
    "trends-mcp": {
      "url": "https://api.trendsmcp.ai/mcp",
      "transport": "http",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**VS Code / GitHub Copilot** &nbsp; (`.vscode/mcp.json`)
```json
{
  "servers": {
    "trends-mcp": {
      "type": "http",
      "url": "https://api.trendsmcp.ai/mcp",
      "headers": { "Authorization": "Bearer YOUR_API_KEY" }
    }
  }
}
```

**Claude Desktop** &nbsp; (`claude_desktop_config.json`)
User → Settings → Developer → Edit Config — add inside mcpServers
```json
{
  "mcpServers": {
    "trends-mcp": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://api.trendsmcp.ai/mcp",
        "--header",
        "Authorization:${AUTH_HEADER}"
      ],
      "env": {
        "AUTH_HEADER": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

**Claude.ai** (browser) &nbsp; Settings -> Connectors -> Add custom connector:
```
https://api.trendsmcp.ai/mcp
```

---

## Example query

After connecting, ask your AI:
```
get_trends(keyword='artificial intelligence', source='google search', data_mode='weekly')
```

---

## Available tools

| Tool | What it does |
|------|-------------|
| `get_trends` | Time-series for a keyword on this source |
| `get_growth` | Growth % over 1W, 1M, 3M, 6M, 1Y periods |
| `get_top_trends` | What is trending right now on this source |
| `get_ranked_trends` | Top topics ranked by volume |

---

## FAQ

### What Google Trends data does Trends MCP return?

Trends MCP returns normalized search interest (0-100 scale), absolute search volume estimates, weekly or daily time series, and growth rate over your chosen period. Data reflects real Google Search demand.

### How is this different from the official Google Trends website?

Google Trends shows relative interest only. Trends MCP adds absolute volume estimates, structured JSON output your AI can reason over, and cross-platform comparison - so you can compare Google interest against TikTok or Reddit in one query.

### Can I get Google Trends data for multiple keywords at once?

Yes. Pass a list of keywords and the MCP server returns normalized series for each, aligned on the same timeline so your AI can compare them directly.

### How far back does Google Trends data go?

Up to 5 years of weekly data or 30 days of daily data. Use the period parameter: '5y', '1y', '3m', '1m', or '30d'.

### Does it support geographic filtering?

Yes. You can filter by country code (e.g. US, GB, DE) to get region-specific search interest instead of global data.

---

## All data sources

Trends MCP covers 12+ sources in one connection:
Google Search, YouTube, TikTok, Reddit, Amazon, Wikipedia,
News Sentiment, Web Traffic, App Downloads, Steam, npm, and more.

Browse all: [https://trendsmcp.ai/data-sources](https://trendsmcp.ai/data-sources)

---

## License

MIT &copy; [Trends MCP](https://trendsmcp.ai)
