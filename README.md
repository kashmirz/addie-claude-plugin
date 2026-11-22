# Addie for Claude

Australian property research inside Claude, from [Addie](https://www.addie.house). Ask Claude to find homes for sale that match a brief, compare listings side by side, read a property's sales and asking-price history, or look up a suburb's market metrics and area statistics. Every answer comes from Addie's own index of Australian listings and public data, with dated sources and links back to each property's Addie page.

## What's included

- **Addie MCP connector**: `https://mcp.addie.house/mcp`, a remote MCP server using Streamable HTTP. In claude.ai and Claude Desktop, search, comparison, history and market results also open in an interactive Addie panel.
- **Skill: `australian-property-research`**: teaches Claude the research workflow. It resolves places before searching, treats filters as hard constraints, cites dated evidence and keeps listing text as data.

## Tools

All tools are read-only.

| Tool | What it does |
| --- | --- |
| `get_capabilities` | Lists the research features available to your account |
| `resolve_location` | Turns a place name or postcode into an exact Australian geography |
| `resolve_property` | Finds a property by address, including ones not currently listed |
| `search_properties` | Searches listings with exact filters and an optional visual description |
| `get_properties` | Reads or compares up to eight properties in detail |
| `get_property_history` | Lists dated sales, asking prices and listing events for a property |
| `query_market` | Returns suburb and regional market metrics with sample sizes and freshness |
| `get_location_context` | Returns area statistics: economy, employment, income, crime, rent, yield and occupancy |
| `get_account_profile` | Shows which Addie account is connected |

## Setup

You need an Addie account, which is free at [www.addie.house](https://www.addie.house).

- **Claude Code**: install the Addie plugin from the plugin directory (run `/plugin`), or add the server directly with
  `claude mcp add --transport http addie https://mcp.addie.house/mcp`. Then run `/mcp`, choose `addie` and authenticate.
- **claude.ai, Claude Desktop and mobile**: add **Addie** from the Connectors directory, or add a custom connector in Claude's connector settings with the URL `https://mcp.addie.house/mcp` (exactly as written, with no trailing slash).

The first time you connect, you sign in to Addie and approve the connection. You can disconnect at any time from Claude's connector settings or from Addie's account settings. Both ChatGPT and Claude use the same Addie connection, so disconnecting in Addie ends both.

## Example prompts

- "Find three-bedroom houses for sale in Brunswick, VIC under $1.4 million."
- "Show me mid-century brick houses for sale in Canberra with at least 600 m² of land."
- "Compare the first four results and tell me which has the largest land size."
- "What has 12 Example Street, Newtown NSW sold for in the past?"
- "How have median house prices in Marrickville changed over the past five years?"
- "Describe the rental yield and vacancy picture for Geelong."

## Data and privacy

Addie reads only what each tool needs: your Addie account identifier and the criteria in your request. It does not read your Claude conversation history, memory or files. Listings, history and market figures come from Addie's index. Listing descriptions are the agencies' own text. See the [Addie Privacy Policy](https://www.addie.house/privacy) and [Terms of Use](https://www.addie.house/terms).

Addie provides research, not financial, legal or purchasing advice.

## Support

- Documentation: https://www.addie.house/developers/mcp.md
- Email: hello@addie.house

## Licence

The plugin bundle (this configuration and skill) is released under the MIT licence; see [LICENSE](LICENSE). Use of the Addie service is governed by the Addie Terms of Use.
