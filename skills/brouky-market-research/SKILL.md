---
name: brouky-market-research
description: Venture market research with Brouky. Use when the user asks how much was raised in a country or sector, for funding trends, the most active or best investors in a country, recent rounds, acquisitions and exits, serial founders, Brouky's articles and reports, or startup and investor events in a city.
---

# Venture market research

Pick the cheapest tool that answers the question, and say where the numbers come from.

## Numbers and trends

- **A country at a glance**: `country_overview` (free). Rounds, money, stages, sectors, top investors since 2020.
- **Any count, total, ranking or trend**: `ask` in plain language (paid, 1 credit). "How many seed
  rounds were there in Germany each year since 2020? Chart it." The answer carries chart specs:
  render them, or describe the shape if charts are not available.
- **The best investors in a country**: `vc_rankings` (free), scored on deal volume, check-size fit,
  portfolio outcomes and risk.
- **The deals behind a trend**: `search_rounds` (free), filtered by country, sector, stage, investor
  and dates. For counts and totals use `ask`, not a tally of `search_rounds` rows.
- **Exits**: `search_acquisitions` (free), by startup, acquirer, country or year.
- **Full report**: `premium_report` for a country or a topic (spacetech, climate ...). Free on paid
  plans, otherwise 10 credits once; `unlock: true` spends them, so ask first. Leave `name` out with
  `kind: "topic"` to list the topics.

## What Brouky has already written

Call `search_insights` first whenever the user asks for Brouky's articles, research or reports on a
topic. Quote the finding and link the article.

## People and places

- **Founders**: `search_founders` (by name, company, country and sector, or serial founders only),
  `get_founder` for one in full.
- **Ecosystem**: `search_organizations` for accelerators, programmes, universities, service providers
  and advisers.
- **Events**: `search_events` by city, country, topic or date ("where can I meet investors in Prague
  next month"), then `get_event` for the speakers, judges and investors taking part.

## Reading the data

- Amounts are facts from a source. A round with no stated amount stays "not disclosed": never
  estimate it, and do not count it in a total.
- A round's stage may be estimated from its amount when the source gives no stage.
- Data starts in 2020. Treat the current year as year to date when comparing it with full years.
- Share each result's `url` so the user can open the full view with charts.
