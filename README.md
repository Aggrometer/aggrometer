# Aggrometer — the gaming attention graph

**Live cross-platform gaming market data for humans and AI agents.** Aggrometer continuously measures ~2,000 games: **Steam concurrent players** (hourly) and **Twitch live viewership** (15-min, game-level aggregates), plus prices, discounts, top-seller ranks, clip velocity, review counts, and pre-release hype — joined per game.

**Signature metric: `aggro` = live viewers ÷ concurrent players, same hour.** Above 1.0, a game holds more audience than players — the signal that streamer marketing converts, that a spectacle moment is happening, or that attention is arriving ahead of sales.

🌐 **[aggrometer.com](https://aggrometer.com)** · [API index](https://aggrometer.com/v1) · [OpenAPI](https://aggrometer.com/v1/openapi.json) · [llms.txt](https://aggrometer.com/llms.txt) · [Pricing](https://aggrometer.com/#pricing)

## MCP server

Remote, streamable HTTP, stateless — 8 read-only tools:

`get_summary` · `top_played` · `top_watched` · `aggro_board` · `genre_rollup` · `hype_board` · `game_detail` · `search_games`

**Endpoint:** `https://aggrometer.com/mcp`
**Auth:** `Authorization: Bearer <your aggrometer API key>` — [get a key](https://aggrometer.com/#pricing) (Basic $3.99/mo · Pro $29/mo · prepaid agent credits $9.99/1,000 queries)

### Claude Code

```bash
claude mcp add --transport http aggrometer https://aggrometer.com/mcp --header "Authorization: Bearer YOUR_KEY"
```

### Claude Desktop / other MCP clients (config JSON)

```json
{
  "mcpServers": {
    "aggrometer": {
      "url": "https://aggrometer.com/mcp",
      "headers": { "Authorization": "Bearer YOUR_KEY" }
    }
  }
}
```

### Cursor

This repo ships a [.mcp.json](.mcp.json) — set the `AGGROMETER_API_KEY` environment variable and Cursor picks it up.

## REST API

Same key, plain JSON:

```bash
curl -H "Authorization: Bearer YOUR_KEY" "https://aggrometer.com/v1/boards/aggro?genre=RPG"
```

Full endpoint index (self-describing, no auth): [`GET /v1`](https://aggrometer.com/v1) · [OpenAPI spec](https://aggrometer.com/v1/openapi.json)

## Also on Apify

Pay-per-query without an Aggrometer key: [apify.com/aggrometer/aggrometer-gaming-attention-data](https://apify.com/aggrometer/aggrometer-gaming-attention-data) — agent-callable via Apify's MCP, x402-payable.

## Who uses this

- **Game developers & publishers** — genre whitespace, launch scouting, competitor attention
- **Marketing teams** — watched-vs-played balance, per game and genre
- **Analysts & press** — attention momentum, hype pipelines, discount effects
- **AI agents** — all of the above, autonomously

## Data notes

Game-level derived aggregates and estimates only. History accrues continuously since 2026-08-26; sparse series indicate a young warehouse, not missing coverage. Live viewership data provided by Twitch; anticipation data provided by IGDB.com.

## Support

support@aggrometer.com
