---
description: Generate the daily morning briefing and save it to briefings/YYYY-MM-DD.md
allowed-tools: Read, Write, Glob, Grep, WebSearch, WebFetch, Bash(git:*), Bash(date:*)
---

Generate today's morning briefing for Kameron. Today's date: run `date +%Y-%m-%d` to get it.

## Gather the four sections

1. **Today's schedule** — Read `notes/reminders.md`. Pull out anything dated today or overdue, plus anything in the "Recurring" section that applies to today's weekday. If the file is empty or has nothing for today, say so in one line.

2. **Novaly trend watch** — Run 2-3 web searches for streetwear / drop-culture / luxury-fashion news from the **last 24 hours** (include today's date in queries). Prioritize: brand collabs, viral drops, resale market moves, celebrity co-signs, and aesthetic shifts relevant to a streetwear-luxury brand. Then flag **1-2 concrete content ideas for @novaly.us** tied to what's trending — each idea should be one sentence with a format (e.g., "carousel breaking down X", "POV reel about Y").

3. **Freelance pipeline** — Read `pipeline/prospects.md`. List any follow-ups whose date is today or past. Then suggest **one specific outreach action** for today (e.g., a niche to prospect like landscaping, roofing, med spas, local gyms — rotate so it's not the same every day; check the last few files in `briefings/` to avoid repeats).

4. **One marketing insight** — One actionable tip on ads, hooks, or funnels that can be applied today. Make it specific (a tactic, not a platitude). Vary the topic day to day; check recent briefings to avoid repeating.

## Output rules

- **Under 300 words total.** Scannable: short headers, bullets, bold the action items.
- Include source links for trend items as markdown links.
- Save it as `briefings/YYYY-MM-DD.md` (today's date).
- If running in CI (the `GITHUB_ACTIONS` env var is set), commit the new file with message `Morning briefing YYYY-MM-DD` and push to `main`.
