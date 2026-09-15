# Daily Scrims

Daily Scrims are scrims that **reset every day**. Each day gets a fresh set of slots and its own leaderboard; rosters are snapshotted per day so historical results survive the reset.

Open the manager with `/dailyscrim` (aliases `dscrim`, `dailyscrims`, `ds`). Requires `daily-scrims-mod` or Manage Server. Note: `daily-scrims-mod` is created by `/setup`, but is **not** accepted by `ssverify`/`tagcheck`/`customform` gating — those check the other three mod roles.

<!-- screenshot: bot-daily-scrims-manager -->

## The Daily Scrims Manager panel

| Button | What it does |
| --- | --- |
| **Create Scrim** | Starts the setup wizard |
| **Edit Settings** | Opens the editor |
| **Instant Start/Stop Reg** | Toggle registration |
| **Reserve Slots** | Hold slots for specific users |
| **Ban/Unban** | Manage banned teams |
| **Drop Location** | Configure the required drop-location setting |
| **Design** | Customize open/close messages |
| **Manage Slotlist** | Repost/refresh the slot list |
| **Scrims Role** | Configure the success role |
| **Public Slot Manager** | Post the live public slot panel to a channel |
| **Groups & Matches** | Group and match management per day |
| **Leaderboard** | Publish standings — today, a past day, or a single group; embed or point-table image, with preview before publishing (same flow as tournaments) |
| **Enable/Disable** | Toggle the whole daily scrim (multi-select) |
| **Analyze Scrims (Test Mode)** | Diagnostics panel for troubleshooting |

## Creating a daily scrim

The setup wizard collects the same core settings as a regular scrim (name, channels, success role, required mentions, slots, open time, game) plus daily-specific settings:

- **Require drop location** — whether registration messages must include a drop location.
- **Rounds per day** — matches per day.

One day-scoring model applies: slots, groups, and results reset daily; per-day rosters are snapshotted into each day's record; the leaderboard defaults to the current day with history preserved per day.

## The public slot manager

**Public Slot Manager** posts a persistent panel to a channel of your choice:

- Shows live slot availability for the current day.
- Lets team leaders claim or cancel a slot with a button — no registration message needed.
- Updates in place as slots fill, and survives bot restarts.

This is the recommended registration flow for daily scrims in large communities.

## Daily cycle

1. At the daily reset, a new day record is created; slots and groups reset.
2. Registration opens at the configured time (or via **Instant Start/Stop Reg**).
3. Teams register (message-based in the reg. channel, or button-based via the public slot manager).
4. **Groups & Matches** manages the current day's groups: send slotlists, ID passes, open/close screenshot windows, process screenshots.
5. **Leaderboard** publishes standings for today, a past day, or a single group — as a quick embed or a styled point-table image, previewed before publishing.
6. The next day starts fresh; previous results remain queryable on the dashboard's daily-scrims pages.

## Managing from the dashboard

Daily scrims are fully manageable at `/daily-scrims` on the dashboard: CRUD, slots, per-day results, and leaderboard. See [Dashboard: Daily Scrims](../dashboard/daily-scrims.md). Daily scrims are subscription-backed like every other event type — creation and match quotas apply per plan.
