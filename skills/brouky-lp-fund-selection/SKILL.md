---
name: brouky-lp-fund-selection
description: Fund selection and LP work with Brouky. Use when a limited partner (fund of funds, family office, institution, corporate) asks which VC funds to back, for due diligence or a memo on a VC fund, how a fund compares with similar funds, who co-invests with or follows on after a fund, about their own LP pipeline, commitments or look-through exposure; or when a VC raising a fund asks which LPs to approach or who backed a fund.
---

# LPs choosing VC funds, and VCs looking for LPs

Call `my_context` first. `lp_workspace` says whether the account has an LP workspace; the LP tools
work from it (its saved investment strategy sets the default filters). Without one, the LP tools
answer `no_lp_workspace` with the link to create one for free: say so in one sentence and offer
`search_investors` / `vc_rankings` for a public view instead.

## For LPs

| Request | Tool |
|---|---|
| Which VC funds fit my programme, funds raising now, emerging managers in a region or sector | `lp_find_funds` (filters default to the saved strategy; any filter you pass replaces that part) |
| Due diligence on one fund: track record, graduation, exits, losses, pace, fund sizes, who follows on, co-investors, similar funds as benchmarks | `lp_fund` |
| A written diligence memo | `lp_fund_memo` (slow the first time, then cached; only when asked for a memo or write-up) |
| Partners, IR person, contact emails | `get_investor` |
| My pipeline, follow-ups, committed funds, look-through exposure, overlap between my managers | `my_lp_pipeline` |
| Add a fund, move it to contacted / meeting / diligence / committed / passed, set a next step | `update_lp_pipeline` (only when the user asks for that change) |

- Judge a manager on the facts `lp_fund` returns, each with its count: graduation to the next round
  against the cohort, exits, shut-downs, survival, follow-on investor quality, pace (new first cheques
  in 12 months) and the peer percentiles. Compare against the `benchmark.similar` funds, not a guess.
- **Fund returns (TVPI, DPI, IRR) are not public and Brouky does not have them.** Say so; never
  estimate them. A fund size is a quoted fact from `vehicles` (with its source); if none is on record,
  say there is none rather than inferring one from deal sizes.
- Share the `url`: it opens the fund page or the Find funds screen in the LP workspace.

## For VCs raising a fund

`find_lps` lists organisations that back venture funds: funds of funds, development banks and public
funds (EIF, KfW Capital, British Business Bank), family offices, pensions, insurers, corporates, banks.
Each comes with the public page that proves it and the funds it backed.

- No filters on a VC account: LPs that backed the funds most similar to the user's own fund, ranked by
  how many such funds they backed. `backed` lists the LPs of a named fund; `kind`, `country` and
  `query` narrow the list.
- Paid plans see websites, IR pages and generic contact emails; free accounts get the top 5 names and
  a notice. Never invent a contact person: the list holds organisations only.
