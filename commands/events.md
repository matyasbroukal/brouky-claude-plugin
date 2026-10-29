---
description: Startup and investor events, with the investors taking part
argument-hint: "<city, country or topic, optionally a month>"
---

Find events with Brouky for: $ARGUMENTS

Call `search_events` with the place (`city`, or `country`, which also takes regions like DACH or
CEE), `topic` and dates (`from_date`, `to_date`) the user gave, and `with_investors_only: true`. If
that finds fewer than three, search again without it. List the events with date, place and how many
known investors take part, best first. For the top ones call `get_event` and name the investors
speaking, judging or attending, with their Brouky links. Give each event's registration link.
