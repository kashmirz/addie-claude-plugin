# Addie Property for Claude

Bring unbiased, live Australian real estate and property research — and your actual Addie buying workflow — straight into Claude (claude.ai, Claude Desktop, mobile, Cowork and Claude Code), powered by [Addie](https://www.addie.house).

Instead of piecing together stale web snippets across portal tabs, Claude queries Addie's live Australian real estate and property index with objective, ad-free search ranking, strict hard filters, visual search, floor plans, upcoming auction dates and venues, dated sales and asking-price revision history, national public school catchments, and cited suburb market data. Link your free Addie account and Claude can also turn your conversation into running Addie buyer briefs, live property alerts, named watchlists (including off-market addresses), weekend inspection schedules and approved agent enquiries — all synced back to Addie.

## Why use Addie in Claude

- **Objective, ad-free search ranking:** Unlike traditional Australian property portals, Addie’s search ranking is never influenced by advertising spend or paid placement from real estate agents or vendors — so results are ordered strictly by relevance to your brief.
- **Search by exact physical criteria *and* how a home looks:** Enforce hard constraints that portals scatter or hide — suburb, postcode, region, radius or polygon, AUD budget, bedrooms, bathrooms, parking, land size, building coverage, pre-market status, street frontage direction, corner lot, rear access, and aerial-detected pool or solar — then rank results by a plain-English visual description such as *"mid-century brick with clerestory windows"*. Filters are never silently relaxed.
- **Run instant due diligence on any address or pasted Addie link:** Paste shared Addie URLs or Australian street addresses (including homes not currently listed) to compare up to eight properties side by side with descriptions, land and building sizes, floor plans, upcoming auction dates and venues, photos, agent contacts, and dated sales, asking-price reduction, withdrawal and rental history.
- **Ground suburb, school-zone and investment analysis in dated evidence:** Compare up to five suburbs, postcodes, LGAs, SA2–SA4 regions, cities or states across 23 sale, rental and inventory metrics (median price, price per square metre, days on market, 12-month price change, price-reduction share, median rent, bond turnover, months of supply and absorption rate) plus public primary and secondary school catchments (with official state/territory lookup links) and aggregate economic, employment, income, crime, rent, yield and occupancy context.
- **Move from chat straight into action (linked account):** Save a researched brief as a live Addie alert, triage newly matched homes and price drops since your last visit, maintain watchlists and upcoming inspection/auction schedules, and check or send approved agent messages — under four independent permissions you control in Addie settings.

## What's included

- **Addie MCP connector**: `https://mcp.addie.house/mcp?access=account`, a remote MCP server using Streamable HTTP. In claude.ai and Claude Desktop, search, comparison, history, market and area results open in an interactive Addie panel with verified listing photos, refinements, sortable comparisons, interactive trend charts and a map.
- **Reusable MCP prompts**: `find_homes`, `compare_properties`, `property_history`, `suburb_research` and (when signed in) `review_buyer_briefs` for one-click structured workflows in Claude Desktop and Claude Code.
- **Skill: `australian-property-research`**: teaches Claude the end-to-end Australian property research and account workflow — resolving places and pasted Addie links accurately, confirming published prices against budgets, citing dated evidence and school catchment lookup portals, keeping listing text as untrusted data, and confirming alert and message actions before acting.

## Example workflows & prompts

### 1. Discover homes by physical brief + visual style

- *"Find 3-bedroom houses for sale in Brunswick or Coburg, VIC under $1.4 million with at least 450 m² of land, rear access, and a bright renovated timber kitchen."*
- *"Show me mid-century brick houses for sale in Canberra with at least 600 m² of land and a pool or solar."*
- *"Search pre-market 4-bedroom houses on corner blocks within 5 km of Manly NSW under $3.5 million."*

### 2. Compare shortlisted homes & uncover auction dates, price drops or sales history

- *"Compare these three Addie property links side by side — land size, floor plan layout, upcoming auction date, published asking price vs. last recorded sale, and whether any has had an asking-price reduction."*
- *"Compare the first four search results and tell me which has the largest land area, best floor plan for a home office, and cleanest pricing history."*
- *"What has 12 Example Street, Newtown NSW sold or been listed for in the past, and has it ever been withdrawn?"*

### 3. Compare suburbs, check public school catchments & evaluate an area

- *"Compare 5-year median house price growth, days on market, price-reduction share and months of supply across Marrickville, Dulwich Hill and Earlwood NSW."*
- *"Which public primary and secondary school catchments cover Paddington QLD for 2026, and how do median rents, household income and crime compare?"*
- *"Describe the rental yield, median rent, bond turnover, household income and crime picture for Geelong vs. Ballarat."*

### 4. Turn research into live Addie briefs, alerts & weekly triage *(linked account)*

- *"Save that Brunswick/Coburg search as a draft buyer brief, preview what matches right now, and show me my alert delivery choices before activating it."*
- *"What new listings or price drops have matched my buyer briefs since last week? Walk me through the unreviewed homes."*

### 5. Track watchlists, off-market homes & weekend inspections *(linked account)*

- *"Add the top two homes to a new 'Saturday inspections' watchlist with price-change alerts, and also add 8 Example Road, Fitzroy VIC off-market."*
- *"Pull my upcoming inspection and auction schedule across my saved homes."*

### 6. Follow up with agents from your Addie inbox *(linked account)*

- *"Check if the agent replied about the Paddington terrace and summarise what they sent."*
- *"Draft an enquiry to the listing agent asking for the contract of sale, strata report and Saturday inspection time — show me the exact wording before sending."*

## Setup

You can research Australian homes as a guest without signing in. To create or manage buyer briefs, alerts, watchlists or messages, sign in with a free [Addie account](https://www.addie.house).

- **Claude Code with the bundled skill**: clone this repository and load it into a session with `claude --plugin-dir ./addie-claude-plugin` from the parent directory. Open `/mcp` and sign in to the Addie server.
- **Claude Code with only the MCP server**: add the server directly with
  `claude mcp add --transport http addie 'https://mcp.addie.house/mcp?access=account'`. Then run `/mcp`, choose `addie` and authenticate.
- **claude.ai, Claude Desktop and mobile**: add a custom web connector in Claude's connector settings with the account URL `https://mcp.addie.house/mcp?access=account` and choose OAuth.

The canonical OAuth resource is `https://mcp.addie.house/mcp`. For guest-only public research, configure `https://mcp.addie.house/mcp?access=public` and choose no authentication.

The first time you connect your account, you sign in to Addie and approve the connection. You can disconnect at any time from Claude's connector settings or from Addie's account settings. Both ChatGPT and Claude use the same Addie connection, so disconnecting in Addie ends both.

Use the permission link returned by a private tool — or open Addie **Settings → Assistant access** — to choose independently whether Claude can manage briefs and alerts, manage watchlists, read your inbox, or send messages.

## Tools

Public research tools work for guests and signed-in accounts. Account tools require a signed-in Addie account and the matching permission group in **Settings → Assistant access**.

### Public research

| Tool | What it does |
| --- | --- |
| `get_capabilities` | Lists the research features and source coverage available to your connection |
| `resolve_location` | Turns a place name or postcode into an exact Australian geography |
| `resolve_property` | Resolves a shared Addie property URL or Australian street address, including homes not currently listed |
| `search_properties` | Searches listings with exact physical and price filters plus an optional visual description |
| `get_properties` | Reads or compares up to eight properties in detail, including descriptions, sizes, floor plans, upcoming auction dates/venues, photos and agent contacts |
| `get_property_history` | Lists dated sales, asking-price revisions, listing campaigns, withdrawals and rental events for a property |
| `query_market` | Returns suburb and regional market, rental and inventory metrics with sample sizes and freshness |
| `get_location_context` | Returns aggregate area statistics (economy, employment, income, crime, rent, yield, occupancy) and suburb public school catchments |

### Account & permissions

| Tool | What it does |
| --- | --- |
| `get_account_profile` | Shows which Addie account is connected |
| `get_workspace_access` | Shows the current client’s four account permissions and Addie settings link |

### Buyer briefs, alerts & review queue

| Tool | What it does |
| --- | --- |
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

### Watchlists & inspection schedule

| Tool | What it does |
| --- | --- |
| `list_watchlists` | List the owner's watchlists, including their default watchlist |
| `get_watchlist` | Read a watchlist and a page of its saved homes, notes, tags and watch preferences |
| `create_watchlist` | Create a named watchlist |
| `update_watchlist` | Rename, edit, archive or restore an owned watchlist |
| `save_watchlist_property` | Save a listing or an off-market address to a named or default watchlist |
| `edit_watchlist_property` | Replace or clear notes and tags on a saved property, or change its notifications for price changes, status changes and new analysis |
| `remove_watchlist_property` | Remove the selected property from its watchlist |
| `get_watchlist_schedule` | Read upcoming inspections and auctions for the owner's saved homes |

### Addie inbox & messaging

| Tool | What it does |
| --- | --- |
| `list_conversations` | List Addie conversations and recent message previews |
| `read_conversation` | Read the newest page of a selected conversation, then use the cursor for older messages |
| `update_conversation` | Mark an owned conversation read, change mute settings, archive or restore it |
| `find_message_recipients` | Find an eligible agent, existing contact or conversation participant by name |
| `upload_message_photo` | Prepare a message photo inline or obtain its private upload URL |
| `complete_message_photo` | Process a photo after transferring it to the private upload URL |
| `read_message_photo` | Read a private photo from a conversation the account participates in |
| `send_message` | Send the user's approved text to one specified recipient or existing conversation |

## Data and privacy

Addie returns only the account records requested by the tools you authorise. A message send delivers your approved text to the selected recipient and may trigger email or in-app notifications. Photos you choose to send are stored privately by Addie and shared with the conversation participants. Listings, history, school catchments and market figures come from Addie's index and official public datasets. Listing descriptions are the agencies' own text. See the [Addie Privacy Policy](https://www.addie.house/privacy) and [Terms of Use](https://www.addie.house/terms).

Addie covers Australia only and provides research, not financial, legal or purchasing advice.

## Support

- Documentation: https://www.addie.house/developers/mcp
- Markdown reference: https://www.addie.house/developers/mcp.md
- Email: hello@addie.house

## Licence

The plugin bundle (this configuration and skill) is released under the MIT licence; see [LICENSE](LICENSE). Use of the Addie service is governed by the Addie Terms of Use.
