# morion

Personal automation repo. Main feature: a daily **7 AM morning briefing**.

## Morning briefing

Every day at 7:00 AM Central, a GitHub Action runs Claude Code with the
[`/morning-briefing`](.claude/commands/morning-briefing.md) command, which:

1. **Today's schedule** — pulls dated items from [`notes/reminders.md`](notes/reminders.md)
2. **Novaly trend watch** — searches the web for streetwear/drop-culture news
   from the last 24h and flags 1-2 content ideas for @novaly.us
3. **Freelance pipeline** — surfaces due follow-ups from
   [`pipeline/prospects.md`](pipeline/prospects.md) and suggests one outreach action
4. **One marketing insight** — an actionable ads/hooks/funnels tip

The result is committed to `briefings/YYYY-MM-DD.md` (under 300 words, scannable).

### One-time setup (required before it runs)

1. Get an API key at [console.anthropic.com](https://console.anthropic.com)
   (or run `claude setup-token` locally for an OAuth token).
2. In this repo: **Settings → Secrets and variables → Actions → New repository
   secret**, name it `ANTHROPIC_API_KEY`, paste the key.
3. Test it: **Actions → Morning Briefing → Run workflow**.

### Notes

- GitHub cron runs in UTC. The schedule is `0 12 * * *` = 7 AM CDT; change to
  `0 13 * * *` after daylight saving ends (edit
  [`.github/workflows/morning-briefing.yml`](.github/workflows/morning-briefing.yml)).
- There's no live calendar integration — keep `notes/reminders.md` and
  `pipeline/prospects.md` updated; the briefing reads both.
- You can also run `/morning-briefing` manually in any Claude Code session on
  this repo.
- Want the file on your Desktop too? On your Mac, a one-line cron/launchd job
  can `git pull` this repo and copy the latest briefing over — or just star the
  repo and read it on your phone from the GitHub app.
