---
name: development-report
description: Build and summarise an Addie Site Finder development report for one analysed Australian site — each option's status, lot sizes and frontages, retained or new dwellings, the planning controls it was tested against with their sources, how many checks the report lists, and the report's assumptions. Use when the user asks for a development report, the options for a site, or a shareable feasibility summary of a site Site Finder has analysed.
---

# Development report

A development report sets out the development options Site Finder found for one site. It is a screening, not
planning advice, a permit, a valuation or a feasibility study. Follow the general rules in the
`australian-property-research` skill.

## Steps

1. **Find the site.** Use a `siteRef` from a ranking, or call `get_development_site` with a `propertyRef`. If the
   site is `not_analysed`, offer to analyse it: `preview_site_analysis` with `subject`, then the steps of the
   `find-development-sites` skill. If it is `needs_refresh`, its assessment was withdrawn after a rule change and
   has no current outcome: offer to analyse it again before any report.
2. **Check what it needs.** If `conversionRequired` is true, the report is a subdivision report: ask whether the
   user wants one before building it.
3. **Build it only when asked.** Call `start_development_report` with the `siteRef`, a new `requestId` and
   `convertToSubdivision` when the user agreed. Tell the user how many reports remain today.
4. **Wait for it.** Call `get_development_report` with the `report` and `waitSeconds` up to 8 until it is
   `ready` or `failed`.
5. **Summarise.** Give the address and Addie report link, site area and frontage, then each option: its title,
   status, lot count, new dwellings, each lot's area, frontage and access, and the planning controls it was tested
   against with their sources. Say how many checks and trade-offs the report lists for it and that they are on the
   report page (the tool returns their number, not their text). End with the report's assumptions and
   disclaimers, word for word.
