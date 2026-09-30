---
name: brouky-vc-research
description: Use Brouky's MCP tools for fundraising and venture research. Use when the user asks about their own startup, investor shortlist, fund, portfolio or leads, or for investors for a startup, VCs in a country or sector, a market overview, deal sourcing for a fund, a pitch deck review, or any question about venture deals and funding rounds.
---

# Venture research with Brouky

Brouky's tools run on live data about investors, startups and funding rounds since 2020.

## The user's own work comes first

The connection is the user's Brouky account. When they say "my startup", "my investors", "my fund",
"my portfolio" or "my leads", call `my_context` first, then the matching tool, instead of asking them
to describe themselves:

- **Founders**: `my_startup` (profile, deck score, past runs), `my_investor_shortlist` (who stands
  where; flags quiet follow-ups), `update_shortlist` ("mark Credo as contacted"; the only tool that
  changes data, confirm with the user first), and `find_investors` with no website uses their startup.
- **Investors**: `my_fund`, `my_portfolio`, `portfolio_status` (who raises next),
  `find_round_investors` ("co-investors for Victor's next round"; the company is found in their
  portfolio first), `my_deal_pipeline`, `startups_raising_next` (deal flow: startups in the fund's
  focus about to raise; unlocking 5 more costs 10 credits, ask first).
- **Organisations**: `my_leads`, `my_applications`, `find_customers`.

Premium country and topic reports: `premium_report` returns the link, or the price if locked (ask
before `unlock: true`).

If a tool answers `needs_choice`, several companies share the name: ask the user which one and call
again with its website.

## Research tools

- **Investors for a startup**: `find_investors` with the startup's website. If you already know
  what the startup does, pass `sector` (and `subsectors` / `tags`) so the first run matches the
  right market. Check `data.startup.classified_as` in the result: if Brouky misread the company,
  say so and rerun with `sector` set. Free accounts get one run with the top 5 matches; paid plans 3 credits a run, up to 50.
- **Any analytical question** (counts, rankings, trends): `ask` in plain language. Paid plans, 1 credit.
- **Look-ups**: `search_investors`, `get_investor`, `search_startups`, `get_startup`,
  `country_overview`. Free.
- **For investors**: `find_startups_for_fund` (deal sourcing against the fund thesis) and
  `analyze_deck` with a direct link to a PDF or PPTX (then `get_deck_analysis` if it is still
  running). Paid plans, 3 credits each.
- **For service providers**: `find_customers` with a plain-language brief.

Always share the `url` from the result: it opens the full report with charts on brouky.tech.
Tell the user what a paid tool will cost before running it more than once.

## Free and paid accounts

The connection acts as the user's Brouky account. If a tool answers `upgrade_required` or
`insufficient_credits`, tell the user in one sentence, give the link from the message, and do not
retry. When unsure what the account can run, call `my_account` first.
