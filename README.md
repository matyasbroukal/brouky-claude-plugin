# Brouky for Claude

Venture research inside Claude: find the investors that fit a startup, write and track the emails to
them, source deals for a fund, analyse pitch decks, and ask any question about investors, startups
and funding rounds since 2020. Results come from [Brouky](https://brouky.tech)'s database of 44,000+
investors, 135,000+ startups and 120,000+ funding rounds.

## What it adds

- **Brouky MCP server** (`https://api.brouky.tech/functions/v1/mcp`) with Sign in with Brouky
  (OAuth). No API key needed. 47 tools.
- **Five skills** that tell Claude which tool fits a request, what it costs and how to chain them:
  - `brouky-vc-research`: picks the right tool for any venture question.
  - `brouky-investor-outreach`: for founders, from the investor list to emails sent and followed up.
  - `brouky-deal-sourcing`: for investors, Brouky picks, startups about to raise, portfolio raising windows.
  - `brouky-market-research`: rounds, rankings, trends, exits, founders and events for a market.
  - `brouky-lp-fund-selection`: for LPs, VC funds that fit the strategy, fund due diligence and the LP pipeline; for VCs, LPs to approach.
- **Six commands**:

| Command | What it does |
|---|---|
| `/brouky:find-investors [website]` | Investors that fit a startup (yours if no website), with why each fits |
| `/brouky:outreach [investor]` | Who to write to next, or the polished email for one investor |
| `/brouky:deal-flow [focus]` | Startups for your fund: Brouky picks, raising next, portfolio to support |
| `/brouky:market <country or sector>` | A market snapshot: money by year, active investors, notable rounds |
| `/brouky:events <city or topic>` | Events with the investors speaking, judging or attending |
| `/brouky:find-funds [focus]` | For LPs: VC funds that fit the investment strategy, with track record and fund size |

## Tools

| For | Tools |
|---|---|
| Founders | `find_investors`, `my_startup`, `my_investor_shortlist`, `update_shortlist`, `my_outreach`, `my_outreach_emails`, `save_outreach_draft`, `mark_email_sent`, `my_network`, `update_my_network` |
| Investors | `my_fund`, `my_portfolio`, `portfolio_status`, `find_round_investors`, `brouky_recommends`, `startups_raising_next`, `find_startups_for_fund`, `my_deal_pipeline`, `analyze_deck`, `get_deck_analysis` |
| Organisations | `my_leads`, `my_applications`, `find_customers` |
| LPs (funds of funds, family offices) | `lp_find_funds`, `lp_fund`, `lp_fund_memo`, `my_lp_pipeline`, `update_lp_pipeline` |
| VCs raising a fund | `find_lps` |
| Everyone | `ask`, `search_investors`, `get_investor`, `search_startups`, `get_startup`, `search_founders`, `get_founder`, `search_rounds`, `search_acquisitions`, `country_overview`, `vc_rankings`, `search_insights`, `search_events`, `get_event`, `search_organizations`, `premium_report`, `my_context`, `my_account` |

Brouky never sends email: Claude drafts it, you send it with your own mail, and `mark_email_sent`
records it and schedules the follow-up.

## Install

In Claude Code:

```
/plugin marketplace add matyasbroukal/brouky-claude-plugin
/plugin install brouky@brouky
```

Then run `/mcp`, pick `brouky` and choose Authenticate to sign in with your Brouky account.
To update later: `/plugin marketplace update brouky`.

## Plans

A free Brouky account covers the look-ups, country overviews, rankings, rounds, events and one AI
VC Finder run with the top 5 matches. Paid plans unlock full data and the AI tools, billed in
credits: [brouky.tech/features/pricing](https://brouky.tech/features/pricing).

## Try

- "Find investors for https://yourstartup.com, we're raising a seed round in Europe."
- "Who should I write to this week? Polish the draft for the best fit."
- "I know the Productboard founders. Which investors does that open up?"
- "Which of our portfolio companies are due to raise?"
- "How many seed rounds were there in Germany each year since 2020? Chart it."
- "Where can I meet fintech investors in Berlin next month?"

## Privacy and support

Brouky receives only the tool inputs Claude sends (a question, a website, a deck link, an email you
asked to save), never the rest of the conversation. Privacy policy:
[brouky.tech/privacy](https://brouky.tech/privacy). Docs and tutorials:
[brouky.tech/developers/guides](https://brouky.tech/developers/guides). Support:
[brouky.tech/contact](https://brouky.tech/contact) or matyas.broukal@harambe.cz.
