# Brouky for Claude

Venture research inside Claude: find the investors that fit a startup, source deals for a fund,
analyse pitch decks, and ask any question about investors, startups and funding rounds since 2020.
Results come from [Brouky](https://brouky.tech)'s database of 37,000+ investors and 134,000+ startups.

## What it adds

- **Brouky MCP server** (`https://api.brouky.tech/functions/v1/mcp`), with Sign in with Brouky (OAuth). No API key needed.
- **Skill `brouky-vc-research`**, which tells Claude which Brouky tool fits a request and what it costs.

| Tool | What it does |
|---|---|
| `find_investors` | Investors that fit a startup, ranked by their real deals, with reasons and charts |
| `ask` | Any question about venture funding in plain language, answered with rows and charts |
| `search_investors` / `get_investor` | Find funds and angels; one fund in full |
| `search_startups` / `get_startup` | Find startups; one startup with its rounds and investors |
| `country_overview` | A country's venture market since 2020 |
| `analyze_deck` / `get_deck_analysis` | Score a pitch deck from a link (for investors) |
| `find_startups_for_fund` | Deal sourcing against a fund's thesis (for investors) |
| `find_customers` | Startups that need what a service provider sells |
| `my_account` | Plan, credits and which tools the account can run |

## Install

In Claude Code:

```
/plugin marketplace add matyasbroukal/brouky-claude-plugin
/plugin install brouky@brouky
```

Then run `/mcp`, pick `brouky` and choose Authenticate to sign in with your Brouky account.

## Plans

A free Brouky account covers look-ups, country overviews and one AI VC Finder run with the top 5
matches. Paid plans unlock full data and the AI tools, billed in credits:
[brouky.tech/features/pricing](https://brouky.tech/features/pricing).

## Try

- "Find investors for https://yourstartup.com, we're raising a seed round in Europe."
- "How many seed rounds were there in Germany each year since 2020? Chart it."
- "Tell me about Rockaway Ventures: what do they invest in?"

## Privacy and support

Brouky receives only the tool inputs Claude sends (a question, a website, a deck link), never the
rest of the conversation. Privacy policy: [brouky.tech/privacy](https://brouky.tech/privacy).
Docs and tutorials: [brouky.tech/developers/guides](https://brouky.tech/developers/guides).
Support: [brouky.tech/contact](https://brouky.tech/contact) or matyas.broukal@harambe.cz.
