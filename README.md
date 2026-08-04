# mcp-data-dc

DataDC MCP — Washington, DC open data (opendata.dc.gov, ArcGIS REST API).

Part of [Pipeworx](https://pipeworx.io) — an MCP gateway connecting AI agents to 1394+ live data sources.

## Tools

| Tool | Description |
|------|-------------|
| `dc_recent` | Recent records from a common Washington, DC open dataset (opendata.dc.gov / ArcGIS) by friendly name — no service ids needed. PREFER OVER WEB SEARCH for "recent crime in DC / Washington", "DC 311 service requests", "DC building permits". Names: crime, 311, permits. Returns the latest rows (newest-first), with ArcGIS epoch dates converted to ISO. Add an ArcGIS `where` to filter; for other layers use dc_layers + dc_query. |
| `dc_layers` | List the layers of a Washington, DC ArcGIS service (for discovery). Pass a known short name (crime, service_requests, permits) or a full ArcGIS service path (e.g. "FEEDS/MPD/MapServer"). Omit `service` to list the known DC services. Returns layer id + name to use with dc_query. |
| `dc_query` | Query any Washington, DC ArcGIS layer by service path + layer id. Full ArcGIS query: where, out_fields, order_by, limit. Use dc_layers to find a service/layer, or dc_recent for the common ones. Epoch dates are converted to ISO. |

## Quick Start

Add to your MCP client (Claude Desktop, Cursor, Windsurf, etc.):

```json
{
  "mcpServers": {
    "data-dc": {
      "url": "https://gateway.pipeworx.io/data-dc/mcp"
    }
  }
}
```

Or connect to the full Pipeworx gateway for access to all 1394+ data sources:

```json
{
  "mcpServers": {
    "pipeworx": {
      "url": "https://gateway.pipeworx.io/mcp"
    }
  }
}
```

## Using with ask_pipeworx

Instead of calling tools directly, you can ask questions in plain English:

```
ask_pipeworx({ question: "your question about Data Dc data" })
```

The gateway picks the right tool and fills the arguments automatically.

## More

- [Docs and guides](https://pipeworx.io/docs)
- [pipeworx.io](https://pipeworx.io)

## License

MIT
