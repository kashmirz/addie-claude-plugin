# Addie for Claude

Australian property research inside Claude, from [Addie](https://www.addie.house). Ask Claude to find homes for sale that match a brief, compare listings side by side, read a property's sales and asking-price history, or look up a suburb's market metrics and area statistics. Every answer comes from Addie's own index of Australian listings and public data, with dated sources and links back to each property's Addie page.

## What's included

- **Addie MCP connector**: `https://mcp.addie.house/mcp`, a remote MCP server using Streamable HTTP. In claude.ai and Claude Desktop, search, comparison, history and market results also open in an interactive Addie panel.
- **Skill: `australian-property-research`**: teaches Claude the research workflow. It resolves places before searching, treats filters as hard constraints, cites dated evidence and keeps listing text as data.

## Tools

Guests can research properties. Linked accounts can grant this client separate permissions for buyer briefs and alerts, watchlists, inbox management and sending messages.

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
| `get_workspace_access` | Shows the current client’s account permissions and settings link |
| `list_buyer_briefs` | List saved buyer briefs and existing property alerts with their shared IDs and monitoring state |
| `get_buyer_brief` | Read the current buyer brief, revision, alert settings, shortlist and recent match history |
| `interpret_buyer_brief` | Convert the buyer's wording into editable criteria and delivery settings for review |
| `create_buyer_brief` | Save a private draft |
| `update_buyer_brief` | Edit a brief or its alert, activate monitoring, pause, resume or archive it |
| `preview_buyer_brief` | Preview current matching homes and warnings for saved or proposed criteria before activating an alert |
| `record_brief_visit` | Record a visit and establish the comparison window for newly matched homes |
| `get_alert_delivery` | Check which notification channels this account can use |
| `list_alert_matches` | Page through a brief or legacy alert's matched homes, including unreviewed homes |
| `record_brief_home_action` | Update the disposition, notes, inspection or outcome of a home matched or previewed by this brief |
| `get_brief_home` | Read a home's current disposition and association with this buyer brief |
| `record_buyer_review_session` | Open or close an account-wide review |
| `get_buyer_review_digest` | Summarise changes and outstanding homes across briefs |
| `list_buyer_review_queue` | Page through distinct homes and their matching briefs |
| `mark_buyer_homes_reviewed` | Mark the selected home and brief associations reviewed |
| `list_watchlists` | List the owner's watchlists, including their default watchlist |
| `get_watchlist` | Read a watchlist and a page of its saved homes, notes, tags and watch preferences |
| `create_watchlist` | Create a named watchlist |
| `update_watchlist` | Rename, edit, archive or restore an owned watchlist |
| `save_watchlist_property` | Save a listing or an off-market address to a named or default watchlist |
| `edit_watchlist_property` | Edit notes, tags, price, status and new-analysis preferences on a saved watchlist item |
| `remove_watchlist_property` | Remove the selected property from its watchlist |
| `get_watchlist_schedule` | Read upcoming inspections and auctions for the owner's saved homes |
| `list_conversations` | List Addie conversations and recent message previews |
| `read_conversation` | Read the newest page of a selected conversation, then use the cursor for older messages |
| `update_conversation` | Mark an owned conversation read, change mute settings, archive or restore it |
| `find_message_recipients` | Find an eligible agent, existing contact or conversation participant by name |
| `upload_message_photo` | Prepare a message photo inline or obtain its private upload URL |
| `complete_message_photo` | Process a photo after transferring it to the private upload URL |
| `read_message_photo` | Read a private photo from a conversation the account participates in |
| `send_message` | Send the user's approved text to one specified recipient or existing conversation |

## Setup

You need an Addie account, which is free at [www.addie.house](https://www.addie.house).

- **Claude Code**: install the Addie plugin from the plugin directory (run `/plugin`), or add the server directly with
  `claude mcp add --transport http addie 'https://mcp.addie.house/mcp?access=account'`. Then run `/mcp`, choose `addie` and authenticate.
- **claude.ai, Claude Desktop and mobile**: add **Addie** from the Connectors directory, or add a custom connector in Claude's connector settings with the URL `https://mcp.addie.house/mcp` (exactly as written, with no trailing slash).

For guest-only research, configure `https://mcp.addie.house/mcp?access=public` and choose no authentication.

The first time you connect your account, you sign in to Addie and approve the connection. You can disconnect at any time from Claude's connector settings or from Addie's account settings. Both ChatGPT and Claude use the same Addie connection, so disconnecting in Addie ends both.

Use the permission link returned by a private tool to choose what Claude may do. Manage or revoke access in Addie Settings → Assistant access.

## Example prompts

- "Save this as a draft buyer brief, preview its matches and show me the alert delivery choices."
- "Add the second match to my inspection watchlist and turn on price-change alerts."
- "Read the reply from my agent about that home."

- "Find three-bedroom houses for sale in Brunswick, VIC under $1.4 million."
- "Show me mid-century brick houses for sale in Canberra with at least 600 m² of land."
- "Compare the first four results and tell me which has the largest land size."
- "What has 12 Example Street, Newtown NSW sold for in the past?"
- "How have median house prices in Marrickville changed over the past five years?"
- "Describe the rental yield and vacancy picture for Geelong."

## Data and privacy

Addie returns the account records requested by the tools you authorise. A message send delivers your approved text to the selected recipient and may trigger email or in-app notifications. Photos you choose to send are stored privately by Addie and shared with the conversation participants. Listings, history and market figures come from Addie's index. Listing descriptions are the agencies' own text. See the [Addie Privacy Policy](https://www.addie.house/privacy) and [Terms of Use](https://www.addie.house/terms).

Addie provides research, not financial, legal or purchasing advice.

## Support

- Documentation: https://www.addie.house/developers/mcp.md
- Email: hello@addie.house

## Licence

The plugin bundle (this configuration and skill) is released under the MIT licence; see [LICENSE](LICENSE). Use of the Addie service is governed by the Addie Terms of Use.
