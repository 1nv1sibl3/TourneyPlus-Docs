# TourneyPlus Documentation

Welcome to the official user guide for **TourneyPlus** — a subscription-gated esports management platform that runs entirely inside Discord, with a web dashboard for billing and advanced management.

**Current release:** Bot `2.2.0` · Dashboard `2.2.0`

## What TourneyPlus does

TourneyPlus runs four kinds of events, end to end, inside your server:

| Event type | Best for | Lifecycle |
| --- | --- | --- |
| **Scrim** | Recurring weekly practice leagues with tiers, promotions, and relegations | Slots reset weekly; tiers reshuffle |
| **Tournament** | Multi-round, multi-group competitive events with round progression | Create → register → group per round → shuffle to next round → final leaderboard |
| **Single Match** | One-off matches (one round, one group) | Fastest flow: create → register → collect results → publish |
| **Daily Scrim** | Day-resetting scrims with per-day rosters and results | Resets every day; per-day leaderboards |

Around the events sit supporting features: player profiles with per-game identities and achievements, screenshot verification (ssverify), tag check test channels, custom registration forms, team profiles, leaderboards with image templates, and subscription plans with quotas.

## Where to start

- **New to TourneyPlus?** Start with [Getting Started](getting-started/overview.md), then follow the [Quickstart](getting-started/quickstart.md) to run your first event.
- **Manage events in Discord?** Read the [Discord Bot User Guide](discord-bot-user-guide.md).
- **Manage events and billing on the web?** Read the [Dashboard User Guide](dashboard-user-guide.md).
- **Stuck on an error?** Jump to [Bot Troubleshooting](bot/troubleshooting-bot.md) or [Dashboard Troubleshooting](dashboard/troubleshooting-dashboard.md).

## Two control surfaces, one platform

Everything can be driven from Discord using slash commands (or the default `!` prefix), and most management tasks can also be done from the web dashboard at `https://tourneyplus.xyz/dashboard`. The two surfaces stay in sync in real time — actions in the dashboard are applied in Discord within seconds, and vice versa.

Some tasks are surface-specific:

- **Discord only:** interactive manager panels (button-driven), in-channel registration, screenshot submission, screenshot verification, tag check channels.
- **Dashboard only:** purchasing plans, redeeming coupons at checkout, quota usage views, prize pool management, leaderboard image templates.

## Conventions used in this guide

- Commands are shown in slash form (`/tourney`). Every command also works with the prefix (default `!`, e.g. `!tourney`). Aliases are listed per command.
- Times are in **IST (UTC+05:30)** unless stated otherwise.
- Where a screenshot would help, you will find a placeholder comment like `<!-- screenshot: dashboard-tournaments-page -->`. Images are being added over time.
- Terminology follows the [Glossary](getting-started/glossary.md) — the same word always means the same thing across every page.
