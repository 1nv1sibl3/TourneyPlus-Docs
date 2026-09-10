# Glossary

The single source of truth for terminology used across all TourneyPlus documentation. If a page uses one of these terms, this is what it means.

## Events

| Term | Definition |
| --- | --- |
| **Event** | Any TourneyPlus-managed competition: a scrim, tournament, single match, or daily scrim. |
| **Scrim** | A recurring, tier-based practice league with weekly shuffles. |
| **Tournament** | A multi-round event; only advancing teams continue to later rounds. |
| **Single Match (SMM)** | A one-round, one-group event. The fastest flow. |
| **Daily Scrim** | A scrim that resets every day, with per-day rosters and leaderboards. |
| **Round** | A stage of an event. Tournaments have multiple rounds; scrims track rounds per day; a single match has exactly one. |
| **Group** | A subset of teams that play together, with its own role and text channel. Labeled A, B, C, … |
| **Tier** | A level in a scrim league (T1–T5). Each tier contains one or more groups. |

## Registration and slots

| Term | Definition |
| --- | --- |
| **Registration channel** | The channel where teams send registration messages (tag-based) or press the Register button (team-profile based). |
| **Registration window** | The period when registrations are accepted. Opens at the configured open time or manually. |
| **Slot** | A numbered team position in an event. `slot_number` is the canonical identifier across bot and dashboard. |
| **Slot list (slotlist)** | The live-updating list of filled slots posted in the slotlist channel. |
| **Required mentions** | The number of teammates a leader must tag in the registration message. Treated as the total team size (leader included) in team-profile mode. |
| **Reserved slot** | A slot held for a specific user, excluded from general registration. |
| **Standby / queue** | Teams waitlisted when all slots are full. Vacancies fill from the standby queue before new registrations. |
| **On-hold / pending registration** | A registration awaiting teammate profile completion or DM confirmations before it is confirmed. |
| **Success role** | The role granted to players when their registration is confirmed. |
| **Open role** | The role pinged when registration opens. Defaults to `@everyone`. |
| **DM verification (dead account check)** | Optional setting requiring each mentioned teammate to confirm participation via a DM button, filtering out dead/inactive accounts. |
| **Team Profile** | A persistent, editable roster owned by a player per guild per game, used for button-based registration instead of tagging. |
| **Multiregister** | Event setting allowing the same player to register multiple teams. |

## Matches and results

| Term | Definition |
| --- | --- |
| **Match** | A logical match record within an event, with a round index, day index, and optional start time. |
| **Screenshot window** | The period during which team leaders may submit a match screenshot in the group channel. |
| **Screenshot submission** | A captured screenshot record, with statuses: `received`, `processing`, `processed`, `needs_review`, `rejected`. |
| **OCR job** | An AI processing job that extracts rank and kills from a submitted screenshot. |
| **Placement / Rank** | The team's finishing position in a match, extracted by OCR or entered manually. |
| **Kills** | The team's kill count for a match. |
| **Placement points** | Points derived from rank via the placement table (battle-royale games only). |
| **Kill points** | Points equal to the kill count (1 point per kill). |
| **Total points** | `Placement points + Kill points`. The leaderboard sort key. |
| **Result source** | How a result was recorded: `manual`, `ai`, or `hybrid` (AI-parsed, human-adjusted). |
| **ID Pass** | Room ID, password, and map details shared with a group for a match. |

## Leaderboards

| Term | Definition |
| --- | --- |
| **Leaderboard** | Ranked standings computed from match results. Scopes: overall, per round, per day, per group, per match. |
| **Publish** | Post a leaderboard to a Discord channel, as an embed or a styled image. |
| **Point table template** | A reusable visual template for image leaderboards (colors, logo, title styling). |
| **Request Review** | A button on published leaderboards that players can press to flag results for moderators. |
| **Leaderboard history** | The last 20 published snapshots stored per group for audit. |

## Scrims specifics

| Term | Definition |
| --- | --- |
| **Tier preset** | The configured tier structure: 2-tier, 3-tier, 4-tier, or 5-tier. |
| **Shuffle** | The weekly reorganization of teams between tiers/groups based on results. |
| **Promotion / relegation** | Moving up / down a tier after a shuffle. Default movement: T1 bottom 8 down; T2 top 8 up / bottom 16 down; T3 top 16 up / bottom 32 down; T4 top 32 up / bottom 64 down; T5 top 64 up. |
| **Score epoch** | The current scoring week in a scrim. Scores reset each shuffle; kill history is preserved for lifetime stats. |
| **Opt-out** | A team voluntarily leaving the current scrim week, freeing its slot. Subject to the configured opt-out cutoff. |
| **Autoclean** | Optional automatic daily cleanup: purging the registration channel and/or removing the success role from last cycle's players. |

## Accounts and subscriptions

| Term | Definition |
| --- | --- |
| **Player profile** | A persistent per-user record (IGN, game profiles, stats) that survives across events and servers. |
| **IGN** | In-game name. Collected via profile, custom forms, or inline in the registration message. |
| **Plan** | A subscription product (e.g. Free, Basic, Pro) defined by entitlements and quotas. |
| **Entitlement** | A per-plan feature flag or quota (e.g. `event.tournament.create`, `ai.ss.process`). |
| **Assignment** | The binding of a plan to a user, a server, or both, with a start/end window. |
| **Scope** | What an assignment covers: `user`, `server`, or `user_server`. |
| **Quota** | A usage-limited entitlement counted over a period (day / week / month / lifetime). |
| **Usage counter** | The per-quota usage record shown on the dashboard profile. |
| **Trial** | A free-duration plan assignment, optionally limited to once per user or once per server. |
| **Coupon / redeem code** | A code applied at checkout for a discount and/or bonus (top-up) entitlements. |
| **Free plan** | The system-managed baseline plan (`free_default`) every server falls back to. |

## People and permissions

| Term | Definition |
| --- | --- |
| **Host** | The user who created an event. |
| **Team leader** | The user who registered a team; the only member who can submit screenshots or transfer leadership. |
| **Mod roles** | `scrims-mod`, `tourney-mod`, `single-match-mod`, `daily-scrims-mod` — created by `/setup`, one per event type. Holders bypass registration requirements for their event type. |
| **Manage Server** | The Discord permission that grants full TourneyPlus management rights. |
