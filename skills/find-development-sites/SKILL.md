---
name: find-development-sites
description: Find and rank Australian sites with development potential using Addie's Site Finder — subdivision, rear dual occupancy, duplex, townhouse or apartment screening over suburbs, postcodes or councils with land, frontage, slope, overlay, listing and price filters. Use when the user asks where they could subdivide, build a duplex or townhouses, or which listed lots in an area suit a development.
---

# Find development sites

Site Finder runs Addie's automated planning screening over every parcel that matches the user's criteria and ranks
the sites. It is a screening, not planning advice, a permit, a valuation or a feasibility study. Follow the general
rules in the `australian-property-research` skill.

## Steps

1. **Pin the criteria.** You need a state, one to twenty places (suburbs, postcodes or councils, matched with
   `resolve_location`), and the development type: `subdivision`, `rear_dual_occupancy`, `duplex`, `townhouse` or
   `apartment`. Ask for anything missing. Keep every filter the user gave: land size, frontage, slope, facing,
   overlays to include or exclude, listing status (for sale by default) and price.
2. **Preview.** Call `preview_site_analysis` with `area` and `intent`. Nothing runs and nothing is charged.
   - `choose_zones`: show the returned `zonesInArea` and ask which zones to include.
   - `unresolved_locations`: ask which of the suggested place names the user means.
   - `zones_pending` or `count_pending`: call the preview again after `retryAfterSeconds`, with the same criteria.
   - `not_covered`: say that Site Finder does not screen this development type there yet. That is not a finding that
     it is impossible.
3. **Agree before starting.** Tell the user the number of candidate sites, how many new site analyses today's
   allowance covers, that the largest lots are analysed first, and the planning rules' date. Start only after
   they agree: call `start_site_analysis` with the `quote` and a new `requestId`. Reuse the same `requestId` if the
   call times out.
4. **Follow or stop it.** Call `get_site_analysis` with the `job` and `waitSeconds` up to 8 while it runs; tell the
   user it keeps running in their Site Finder on addie.house if they leave. If the user asks to stop an analysis
   started here, call `cancel_site_analysis` with the `job` and a new `requestId` (already-analysed sites stay
   readable and nothing further is charged).
5. **Show the ranking.** Page through results with `cursor`. For each site give the rank, address and Addie link,
   zone, land area, the screening outcome, the estimated lots or dwellings, and the deciding controls with their
   clauses. Say how many sites have caveats or unresolved requirements.
6. **At the daily limit.** Quote `limitMessage`: how many sites were analysed, that the ranking covers only those,
   and when the allowance resets. Offer to continue the next day (`start_site_analysis` with `continueJob`) or
   to finish the search in Site Finder on addie.house.
7. **Earlier work.** `list_site_work` also lists searches the user ran on addie.house or in the app; read their
   rankings with `get_site_analysis`. Only analyses started here can be continued or cancelled here.
8. **Reports.** For a site the user picks, use the `development-report` skill.

## Wording

- Use the outcome words as given: meets the checks, needs review, does not meet, not enough data.
- An off-market site is a parcel, not a seller's intention to sell.
- Never give a probability of approval, a price or a profit.
