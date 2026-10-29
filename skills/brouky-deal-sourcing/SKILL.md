---
name: brouky-deal-sourcing
description: Deal sourcing and portfolio work for investors with Brouky. Use when a VC or angel asks for startups that fit their fund, what Brouky recommended, which startups will raise next, which portfolio companies are due to raise, co-investors for a round, what is in their pipeline, or to score a pitch deck.
---

# Deal sourcing for investors

Call `my_context` first. It names the fund(s) the account belongs to with the saved thesis, stage and
sector focus. If there are several funds, ask which one. Read `my_fund` before judging fit: thesis,
check size, deals by year, lead ratio, median round, top co-investors.

## New deals

| Ask | Tool | Cost |
|---|---|---|
| "What did Brouky recommend for us" | `brouky_recommends`: hand-picked startups with why each one, stage, money raised and asked, whether the founder can be messaged | free |
| "Who is about to raise in our focus" | `startups_raising_next`: next round and why (time since last round, momentum, team, filed revenue against the benchmark, runway) | free for what is unlocked; `unlock_more: true` = 5 more for 10 credits, ask first |
| "Find startups that fit our thesis" | `find_startups_for_fund` | paid, 3 credits |
| "Recent seed deals in fintech in Poland" | `search_rounds` | free |
| "Score this deck" | `analyze_deck` with a direct PDF or PPTX link, then `get_deck_analysis` if it is still running | paid, 3 credits |
| "What is in our pipeline" | `my_deal_pipeline`: data rooms by stage with deck score and verdict | needs a paid plan |

Check a startup's stage against the fund's `stage_focus` before calling it a fit. A Series B company
is not a pick for a pre-seed fund however good the sector match is.

## Portfolio

- **Who raises next**: `portfolio_status` sorts the portfolio into raising window now, overdue,
  recently funded, and closed or exited, from the usual time between rounds at each stage.
- **Co-investors for a portfolio company's round**: `find_round_investors` (the company is found in
  the fund's portfolio first).
- **The whole portfolio**: `my_portfolio`.

## Diligence on any company

`get_startup` (rounds, investors, positioning), `get_founder` (every company the founder started and
who backed it), `search_acquisitions` for exits in the space, `get_investor` for the other funds on
the cap table. Amounts appear only when a source states them; say "amount not disclosed" rather than
guessing.

Share each result's `url`: it opens the full view on brouky.tech.
