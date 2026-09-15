# Scrims

Scrims are TourneyPlus's recurring, tier-based practice leagues. One scrim exists per server; teams register weekly into tier groups, play matches, and shuffle between tiers based on results.

Open the manager with `/scrim` (or `/smanager`, aliases `s`, `sm`). Requires `scrims-mod` or Manage Server.

<!-- screenshot: bot-scrims-manager-panel -->

## The Scrims Manager panel

| Button | What it does |
| --- | --- |
| **Create Scrim** | Starts the scrim setup wizard |
| **Edit Settings** | Opens the editor for an existing scrim |
| **Instant Start/Stop Reg** | Manually open or close registration |
| **Reserve Slots** | Hold slots for specific users |
| **Ban/Unban** | Manage banned teams (with optional timed bans) |
| **Design** | Customize registration open/close messages and colors |
| **Manage Slotlist** | Repost/refresh the slot list |
| **Group Tools** | Open the group management panel (screens, leaderboards, shuffle) |
| **Process On-Hold** | Retry pending registrations (confirm or move to standby) |
| **Send Slot Manager** | Post a persistent public slot-manager panel to a channel |

## Creating a scrim

Only **one scrim per server** is allowed. Click **Create Scrim** in the manager and fill the lettered settings:

| Setting | Notes |
| --- | --- |
| Scrim Name | Display name |
| Reg. Channel | Where registration messages are sent |
| Slotlist Channel | Where the slot list is posted |
| Success Role | Granted on confirmed registration |
| Req. Mentions | Teammates that must be tagged |
| Tier Preset | See tier presets below |
| Open Time | Daily time registration opens (IST) |
| Scrim Days | Days of the week the scrim runs |
| Rounds / Day | Matches per day, and group size |
| Opt-out Cutoff | Hours after the score epoch within which teams may opt out |
| Reactions | Custom accept/reject emojis (premium) |
| Rulebook | Tier movement rules text |
| DM Verification | Require teammates to confirm via DM |
| Registration Type | `Tag based` or `Team Profile` |
| Confirm Channel | Optional confirmation channel |
| Open Role | Role pinged at open time |
| Game | BGMI / FREEFIRE / VALORANT / CS2 |

**Save** enables once reg. channel, slotlist channel, success role, total slots, and open time are set. The wizard autosaves as a draft — if you time out, re-opening **Create Scrim** restores your progress.

<!-- screenshot: bot-scrim-setup-wizard -->

### Tier presets

| Preset | Tier sizes | Total slots | Plan |
| --- | --- | --- | --- |
| 2-tier | T1: 20, T2: 40 | 60 | Free |
| 3-tier | T1: 20, T2: 40, T3: 80 | 140 | Paid |
| 4-tier | T1: 20, T2: 40, T3: 80, T4: 160 | 300 | Paid |
| 5-tier | T1: 20, T2: 40, T3: 80, T4: 160, T5: 320 | 620 | Paid |

Each tier contains groups of the base size (default 20 teams per group).

### Default tier movement (weekly shuffle)

- Tier 1: bottom 8 relegate down.
- Tier 2: top 8 promote up, bottom 16 relegate down.
- Tier 3: top 16 promote up, bottom 32 relegate down.
- Tier 4: top 32 promote up, bottom 64 relegate down.
- Tier 5: top 64 promote up; bottom 64 rotate internally/queue out.

Movement is deterministic: ties break by kills, then earliest registration. The rulebook is customizable via the setup wizard.

## Daily cycle

1. **Open time** — registration opens automatically on configured days (a daily timer re-arms itself).
2. **Slots fill** — registrations occupy the next available slot; when one slot remains, registration auto-closes.
3. **Matches** — schedule matches via Group Tools or the dashboard; send ID passes to groups.
4. **Screenshot window** — open, collect, process (see [Screenshot Flow](screenshot-flow.md)).
5. **Leaderboard** — publish per group/round/day, or overall.
6. **Weekly shuffle** — reshuffle tiers; choose to keep or reset scores (kill history is always preserved for lifetime stats).
7. **Autoclean** (optional) — daily purge of the registration channel and/or removal of the success role.

## Group Tools

The Group Tools panel manages a scrim's groups (created automatically when registration closes):

| Button | What it does |
| --- | --- |
| Group selector / page controls | Pick the active group (paged, 20 per page) |
| **Send ID/Pass** | Post room ID / password / map for the group |
| **Collect Screenshots** / **Stop Collecting** | Open / close the screenshot window |
| **Process Images** | Submit collected screenshots for AI processing |
| **Publish Leaderboard** | Publish standings for the group |
| **Flexible Leaderboard** | Choose scope (round/day/overall) before publishing |
| **Unlock Chat** / **Lock Chat** | Toggle the group channel's write permission for the group role |
| **Organize Groups** | (Re)generate group roles and channels |
| **Shuffle Tiers** | Run a manual tier shuffle — choose Normal (top/bottom per group) or Fill (promote-only), and keep or reset scores |
| **Resync Roles** | Reconcile group role membership with actual rosters (adds missing, strips stale) |
| **Refresh** | Reload the panel |

<!-- screenshot: bot-scrim-group-tools -->

## Slot manager

**Send Slot Manager** posts a persistent public panel that shows live slot status and lets players confirm/cancel their slot without typing in the registration channel. The panel survives bot restarts.

## Bans

From **Ban/Unban** you can ban a user or team from the scrim, optionally with a duration — the bot auto-unbans when the timer expires and logs the unban.

## Managing from the dashboard

Everything above (create/edit, registration, teams, groups, screenshots, shuffle) is also available at `/scrims` on the dashboard — see [Dashboard: Scrims](../dashboard/scrims.md). The two surfaces stay synchronized; the dashboard additionally offers shuffle configuration, shuffle logs, and kicking teams in bulk.
