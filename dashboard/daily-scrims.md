# Dashboard: Daily Scrims

Managing daily scrims from the web at `/daily-scrims`. Requires `daily-scrims-mod` or Discord Manage Server on the selected server.

<!-- screenshot: dashboard-daily-scrims-list -->

## The daily scrims list

Cards per daily scrim showing its state (open / closed / disabled) and slot fill. Actions: open the detail page, delete (with confirmation — removes the event with its slots, reservations, and bans), and **Create Daily Scrim** to start the creation wizard.

## Creating a daily scrim (`/daily-scrims/create`)

The wizard collects:

| Step | Fields |
| --- | --- |
| Channels & roles | Name, registration channel, slotlist channel, success role, public slot-manager channel (optional), ban-log channel (optional), ping role, registration-open role |
| Registration | Team size, total slots, teams per group, matches per group per day, first open date and daily open time (IST), registration mode and reg-open embed style |
| Match lock & autoclean | Daily match-lock time (IST) and autoclean schedule |
| Advanced | Extra organizer options |
| Review | Summary before creating |

All times are IST, matching the bot's daily-reset schedule.

## The detail page

- **Slots** — the current day's slot fill, reservations, and bans.
- **Days** — the per-day history: each day's roster snapshot and results.
- **Matches** — schedule and manage matches for the current day.
- **Leaderboard** — the current day's standings and publishing.

## How daily state works

- The event resets every day: a new day record is created, slots empty, and groups regenerate.
- **Per-day rosters are snapshotted** — each day keeps its own immutable record of who played, so deleting or editing later days never rewrites history.
- Leaderboards default to the current day; previous days remain queryable in the **Days** view.

## Registration

Start/stop registration relays to Discord. Teams register in the configured channel (message-based) or via the public slot manager panel posted from the Discord manager. Slot rules are the same as other events (lowest free slot; canonical `slot_number`).

## Results

The same pipeline as scrims: open the group's screenshot window, collect submissions, process them (AI entitlement permitting), or enter results manually, then publish the day's leaderboard. See [Screenshot Flow & Results](../bot/screenshot-flow.md).

## Notes

- Daily scrims are subscription-backed: creation and match quotas apply per plan.
- The Discord-side manager (`/dailyscrim`) offers the same operations as button panels, including drop-location configuration and the public slot manager.
