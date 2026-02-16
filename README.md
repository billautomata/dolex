# Dolex

**Visualization intelligence for AI.** 43 handcrafted chart patterns — far beyond bar, line, and pie.

Every AI assistant suggests a bar chart. Dolex suggests the *right* chart — bump charts for rankings, beeswarms for distributions, connected dot plots for two-metric comparisons, waffle charts for precise proportions.

## Install

```bash
npm install @outsidedata/dolex
```

## Claude Desktop

Add to `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows):

```json
{
  "mcpServers": {
    "dolex": {
      "command": "npx",
      "args": ["@outsidedata/dolex"]
    }
  }
}
```

Restart Claude Desktop. Dolex's 17 tools appear in the tool picker.

## Claude Code

```bash
claude mcp add dolex -- npx @outsidedata/dolex
```

## Other MCP Clients

Any MCP-compatible client (ChatGPT, VS Code, Goose, etc.) can connect via stdio:

```bash
npx @outsidedata/dolex
```

## What It Does

You give Claude your data and ask a question. Dolex analyzes the data shape and your intent, then picks the right visualization from 43 handcrafted patterns — not the obvious chart, the *informative* one.

Charts render inline in the conversation as interactive HTML. No external dependencies, no CDN calls, fully offline.

### Tools

| Tool | What it does |
|------|-------------|
| `visualize` | Inline data + intent → ranked chart recommendations |
| `visualize_from_source` | Data source + DSL query + intent → chart recommendations |
| `list_patterns` | Browse all 43 patterns |
| `refine_visualization` | Tweak a chart — sort, limit, flip axes, colors, title |
| `add_source` | Connect CSV, SQLite, PostgreSQL, or MySQL |
| `list_sources` | List connected sources |
| `remove_source` | Disconnect a source |
| `describe_source` | Column profiles and sample rows |
| `analyze_source` | Auto-generate an analysis plan with DSL queries |
| `query_source` | Run a declarative query (joins, aggregations, filters) |
| `create_dashboard` | Multi-view dashboard with filters and cross-filtering |
| `refine_dashboard` | Iterate on a dashboard |
| `server_status` | Inspect cached data |
| `clear_cache` | Clear cached specs and results |
| `report_bug` | Generate a sanitized bug report |
| `export_html` | Get raw HTML for a chart |
| `screenshot` | Render a chart to PNG |

### Patterns

| Category | Patterns |
|----------|----------|
| **Comparison** (9) | Bar, Diverging Bar, Slope Chart, Connected Dot Plot, Bump Chart, Lollipop, Bullet, Grouped Bar, Waterfall |
| **Distribution** (7) | Histogram, Beeswarm, Violin, Ridgeline, Strip Plot, Box Plot, Density Plot |
| **Composition** (9) | Stacked Bar, Waffle, Treemap, Sunburst, Circle Pack, Metric, Donut, Marimekko, Icicle |
| **Time** (7) | Line, Area, Small Multiples, Sparkline Grid, Calendar Heatmap, Stream Graph, Horizon Chart |
| **Relationship** (5) | Scatter, Connected Scatter, Parallel Coordinates, Radar, Heatmap |
| **Flow** (4) | Sankey, Alluvial, Chord, Funnel |
| **Geo** (2) | Choropleth, Proportional Symbol |

### Data Connectors

- **CSV** — load local CSV files into an in-memory SQLite database
- **SQLite** — read-only access to SQLite databases
- **PostgreSQL** — connect to Postgres instances
- **MySQL** — connect to MySQL instances

All connectors support the declarative DSL query language with joins, aggregations, groupBy (with time bucketing), filters, orderBy, and limit.

### Offline Maps

33 TopoJSON files ship with the package — world maps, US states/counties, 6 continent maps, and 17 country subdivision maps (Germany, France, Japan, China, etc.). All map data is embedded inline in the chart HTML. No CDN calls, ever.

## License

MIT
