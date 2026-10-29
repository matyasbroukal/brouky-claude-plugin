---
description: "For LPs: VC funds that fit your investment strategy, with track record and fund size"
argument-hint: "[optional: countries, stage, sector, emerging managers, raising now]"
---

Find VC funds for this LP on Brouky. Focus: $ARGUMENTS

Follow the brouky-lp-fund-selection skill. Call `my_context`, then `lp_find_funds` with the focus as
filters (none given: the saved strategy). For the top 3, call `lp_fund` and compare graduation, exits,
pace and fund size with their similar funds. Never state returns (TVPI, DPI, IRR): they are not public.
Say which funds are already in the LP's pipeline, and offer `update_lp_pipeline` to shortlist one.
Share each `url`.
