---
name: brouky-vc-research
description: Use Brouky's MCP tools for fundraising and venture research. Use when the user asks about their own startup, investor shortlist, outreach, fund, portfolio, leads or LP pipeline, for VC funds an LP should back, LPs for a fund, or for investors for a startup, VCs in a country or sector, funding rounds, acquisitions, founders, startup events, a market overview, deal sourcing for a fund, a pitch deck review, or any question about venture deals.
---

# Venture research with Brouky

Brouky's tools run on live data about investors, startups, founders and funding rounds since 2020.
This skill picks the tool. Three workflow skills go deeper:

- **brouky-investor-outreach**: a founder going from "who fits" to emails sent and followed up.
- **brouky-deal-sourcing**: an investor looking for startups, co-investors or portfolio companies about to raise.
- **brouky-market-research**: rounds, rankings, trends, exits, events and reports for a country or sector.
- **brouky-lp-fund-selection**: an LP choosing and monitoring VC funds, or a VC looking for LPs.

## The user's own work comes first

The connection is the user's Brouky account. When they say "my startup", "my investors", "my fund",
"my portfolio", "my drafts" or "my leads", call `my_context` first, then the matching tool, instead
of asking them to describe themselves. `my_context` also lists `useful_tools` for that account.

| Who | Tools |
|---|---|
| Founders | `my_startup`, `my_investor_shortlist`, `update_shortlist`, `my_outreach`, `my_outreach_emails`, `save_outreach_draft`, `mark_email_sent`, `my_network`, `update_my_network`, `find_investors` (no website: uses their startup) |
| Investors | `my_fund`, `my_portfolio`, `portfolio_status`, `find_round_investors`, `brouky_recommends`, `my_deal_pipeline`, `startups_raising_next`, `find_startups_for_fund`, `analyze_deck` / `get_deck_analysis` |
| Organisations and service providers | `my_leads`, `my_applications`, `find_customers` |
| LPs (funds of funds, family offices) with an LP workspace | `lp_find_funds`, `lp_fund`, `lp_fund_memo`, `my_lp_pipeline`, `update_lp_pipeline` |
| VCs raising a fund | `find_lps` |

## Public data

| Question | Tool | Cost |
|---|---|---|
| Investors that fit a startup | `find_investors` | free account: one run, top 5; paid: 3 credits, up to 50 |
| Counts, totals, rankings, trends in plain language | `ask` | paid, 1 credit |
| A fund or angel | `search_investors`, `get_investor` | free |
| A startup | `search_startups`, `get_startup` | free |
| A founder, serial founders | `search_founders`, `get_founder` | free |
| Funding rounds | `search_rounds` | free |
| Acquisitions | `search_acquisitions` | free |
| A country's market | `country_overview`, `vc_rankings` | free |
| Brouky's own articles and research | `search_insights` | free |
| Events where investors speak or attend | `search_events`, `get_event` | free |
| Accelerators, programmes, service providers, advisers | `search_organizations` | free |
| Full country or topic report | `premium_report` | free on paid plans, else 10 credits once |

## Rules that hold for every tool

- **Free tools run at once.** For a free look-up, pick sensible defaults (the last 12 months, the top
  20) and call it; do not ask a clarifying question first. Ask only before spending credits or
  changing the user's data.
- **Paid tools run only when asked.** Never call `find_investors`, `ask`, `find_startups_for_fund`
  or `analyze_deck` as a side step of another request: they spend credits, and `find_investors`
  also adds its matches to the user's shortlist. Offer them instead.
- **Share the `url`** from the result: it opens the full view with charts on brouky.tech.
- **`needs_choice`** means several companies or investors share the name: ask which one, then call
  again with its website or key.
- **Money**: say what a paid tool costs before running it more than once. Anything that unlocks
  (`unlock: true`, `unlock_more: true`) needs the user's yes. Call the tool without the unlock first:
  it says whether the item is already open (often free on paid plans) and the real price. If the
  user already asked to unlock it and the tool names a price, confirm that price once, then unlock.
- **Writes**: `update_shortlist`, `update_my_network`, `update_lp_pipeline`, `save_outreach_draft` and `mark_email_sent`
  change the user's own data. When the user asks for the change in plain words ("Senovo passed",
  "add Seedcamp to my network", "save it"), that is the go-ahead: do it and say what changed. Never
  make a change they did not ask for, and call `mark_email_sent` only after the email really went out.
- **Plans**: on `upgrade_required` or `insufficient_credits`, tell the user in one sentence, give the
  link from the message, and do not retry. When unsure what the account can run, call `my_account`.
- **Amounts** are facts from a source. Rounds without a stated amount stay without one: never fill
  the gap with a guess. A round's stage can be estimated from its amount when the source gives none.
