---
name: brouky-investor-outreach
description: Founder fundraising outreach with Brouky, from the investor list to emails sent and followed up. Use when a founder asks who to write to, wants a draft for a fund, asks how to get an intro to an investor, wants to polish or send investor emails, asks who has not replied or which follow-ups are due, or says who they know ("I know the Productboard founders").
---

# Investor outreach for founders

Brouky never sends an email. Claude writes or polishes it, the user sends it with their own mail,
and Brouky records it so the shortlist and follow-ups stay right.

## 1. Know the startup

Call `my_context`. If the user has several startups, ask which one and pass `startup` from then on.
If the shortlist is empty, run `find_investors` with no website (it uses their startup; free accounts
get one run with the top 5, paid plans 3 credits a run). If `data.startup.classified_as` misreads the
company, say so and rerun with `sector` set.

## 2. Pick who to write to

`my_outreach` returns the investors to write to, warm ones and best fit first, each with:

- `why`: why Brouky matched them.
- `closest_portfolio`: the fund's companies nearest to the user's, with what each does.
- `ways_in`: people who can introduce them, founders the fund backed, the address to write to.
- `deck_link`: a personal deck link for this investor (decks cannot be attached); `deck_read` shows opens.
- `draft`: the saved draft, or the email Brouky's AI wrote.

Use `filter: "warm"` for investors someone the user knows can introduce, `investor: "<name>"` for one
investor in full. A warm way in beats a cold email: suggest the intro first when there is one.

If `my_outreach` answers `not_found`, the investor is not on the user's list yet. Do not stop there:
call `get_investor` for its partners, contact and portfolio, check `my_network` for anyone who knows
them, and offer to add it with `update_shortlist` so Brouky builds its ways in and email.

## 3. Grow the warm paths

When the user names someone they know ("we know Seedcamp", "Petra Novak at Kaya is a friend"), call
`update_my_network`. Pass `at` (their fund or startup) for a common name. The answer names the
investors that just gained a warm way in. `my_network` lists everyone on file.

## 4. Write the email

Start from the draft in `my_outreach` and edit it so it reads like the founder typed it:

- Under 140 words, short sentences, plain text, blank lines between paragraphs.
- Keep the greeting, the named portfolio company and what it does, the ask, the `Deck:` line with
  that investor's `deck_link`, and the sign-off.
- Fix everything listed in `sounds_like_ai`. Cut filler and stock phrases (pain point, leverage,
  innovative, data-driven, in the same space, I would appreciate). Replace vague claims with the
  concrete facts already in the email.
- Add no facts, numbers or names that are not in the draft or from the user.
- Never an em dash. Never an unfilled placeholder like `[phone]`: ask the user or leave it out.

Show the edited email and say in one line what changed.

## 5. Save, send, record

After the user approves:

1. `save_outreach_draft` with `investor`, `subject`, `body` and `to` (it refuses em dashes and
   placeholders; fix any warnings it returns).
2. Send it with the user's own mail tool if one is connected, or hand it over to send.
3. Only once it really went out: `mark_email_sent`. It moves the investor to Contacted and sets a
   follow-up in 5 days (`follow_up_days` to change).

## Follow-ups and status

- "Show my drafts", "who has not replied", "which follow-ups are due": `my_outreach_emails` with
  `drafts`, `waiting` or `sent`.
- "Who have I contacted", "who passed": `my_investor_shortlist`.
- "Rockaway passed", "add a note to Credo": `update_shortlist` right away; the request is the go-ahead. To record a sent
  email use `mark_email_sent` instead, so the email and follow-up are logged too.

Share `https://brouky.tech/dashboard/outreach` (the `url` in the result) so the user can see it all.
