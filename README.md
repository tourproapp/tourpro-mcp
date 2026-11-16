# TourPro MCP server

TourPro's public MCP server: tour management tools for AI clients over
[Streamable HTTP](https://modelcontextprotocol.io) at `https://mcp.tourpro.app/mcp`.

Tour managers, production teams and touring crews can ask an AI assistant about
their next show, pull a day sheet, check open advancing items, and manage
events, tours and day notes — without opening the TourPro app.

## Using it

- **Endpoint**: `https://mcp.tourpro.app/mcp` (stateless Streamable HTTP, POST only)
- **Auth**: OAuth 2.1 with PKCE against TourPro's Auth0 tenant. No API keys.
  Sign in with your own TourPro account; every tool call runs under your role
  and permissions on each tour.
- **Discovery**: `initialize`, `ping` and `tools/list` are answered without a
  token so clients and directories can inspect the tool set before sign-in.
  `tools/call` requires the OAuth token.

## Tools

Reads include `list_my_tours`, `get_next_event`, `get_day_sheet`,
`list_open_items`, `list_events`, `list_day_notes` and `ask_tourpro`
(grounded Q&A over a tour's data). Writes cover events, tours and day notes
with the same permissions the app enforces. The full list:
<https://www.tourpro.app/docs/integrations/tools>

## Links

- Product: <https://www.tourpro.app>
- Claude connector guide: <https://www.tourpro.app/docs/integrations/claude>
- ChatGPT guide: <https://www.tourpro.app/docs/integrations/chatgpt>
- Privacy: <https://www.tourpro.app/privacy>
- Official MCP Registry entry: `app.tourpro/mcp` (see `server.json`)

Source lives in TourPro's private monorepo; this repo holds the public
registry metadata and docs for the server.
