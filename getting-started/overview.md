# Overview

TourneyPlus is an esports management platform for Discord servers. It runs your events end to end — registration, slot management, group creation, match scheduling, result collection, and leaderboards — and pairs with a web dashboard for billing, plan management, and advanced operations.

<!-- screenshot: landing-page-hero -->

## The four event types

| Event type | What it is | When to use it |
| --- | --- | --- |
| **Scrim** | A recurring, tier-based practice league. Teams register weekly, get placed into tier groups (T1–T5), and move up or down based on weekly results. | Regular daily/weekly practice for a community. |
| **Tournament** | A multi-round competitive event. Teams register once, are split into groups per round, and only advancing teams continue to the next round. | Structured competition with a final winner. |
| **Single Match** | One match, one round, one group. The fastest end-to-end flow. | One-off matches, tryouts, showmatches. |
| **Daily Scrim** | A scrim that resets every day. Per-day rosters are snapshotted, and leaderboards are per-day. | Communities that run fresh scrims daily without weekly tier logic. |

All four share the same lifecycle pattern: **create → open registration → fill slots → close registration → run matches → collect results → publish leaderboard**. The differences are in grouping, rounds, and reset behavior.

## Who uses TourneyPlus

- **Server owners / administrators** — set up the bot, manage subscriptions, configure premium branding.
- **Event managers** — create events, control registration, moderate teams, publish results. Identified by the `Manage Server` permission or one of the mod roles below.
- **Moderators** — help run events under a scoped mod role.
- **Team leaders** — register teams, rename teams, transfer leadership, submit screenshots.
- **Players** — maintain a profile, join teams, view stats.

## Mod roles created by setup

Running `/setup` creates four private log channels and four moderator roles:

| Event type | Mod role | Log channel |
| --- | --- | --- |
| Scrim | `scrims-mod` | `tourneyplus-scrims-logs` |
| Tournament | `tourney-mod` | `tourneyplus-tourney-logs` |
| Single Match | `single-match-mod` | `tourneyplus-single-match-logs` |
| Daily Scrim | `daily-scrims-mod` | `tourneyplus-daily-scrims-logs` |

Members with `Manage Server` can always do everything a mod role allows. See [Setup & Permissions](../bot/setup-and-permissions.md).

## How Discord and the dashboard work together

- Most event operations are available **both** in Discord (via manager panels and commands) and on the **web dashboard**.
- The two surfaces synchronize in real time. If an action seems stuck, allow a few seconds and refresh.
- Billing, plan purchases, and quota views are dashboard-only. In-channel registration and screenshot submission are Discord-only.

## Games supported

TourneyPlus currently supports **BGMI, FREEFIRE, VALORANT, and CS2**. Events and forms are tagged with a game, and the dashboard has a global game filter. Note that the rank-based placement points (see [Leaderboards](../bot/leaderboards.md)) apply to battle-royale games (BGMI, FREEFIRE); non-battle-royale games (VALORANT, CS2) score kills only.

## Next steps

- Install the bot and run setup: [Setup & Permissions](../bot/setup-and-permissions.md)
- Run your first event: [Quickstart](quickstart.md)
- Understand the vocabulary: [Glossary](glossary.md)
