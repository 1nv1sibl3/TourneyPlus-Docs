# Dashboard: Scrims

Managing scrims from the web: creation, registration control, teams, groups, screenshots, and shuffles. The page pair is `/scrims` (list) and `/scrims/[id]` (detail/manage), plus `/scrims/config` for creation.

Requires the `scrims-mod` role or Discord Manage Server on the selected server.

<!-- screenshot: dashboard-scrims-list -->

## The scrims list

Cards per scrim showing state (open/closed/disabled), slot fill, game, and next open time. From each card you can open the detail page, organize groups, kick teams, or delete the scrim (with confirmation). Shuffle logs are viewable per scrim.

## Creating a scrim (`/scrims/config`)

A wizard collects:

| Step | Fields |
| --- | --- |
| Basics | Name, registration channel, slotlist channel, description |
| Schedule | Open time, scrim days, timezone handling (IST) |
| Structure | Tier preset (2/3/4/5-tier; see the tier table in [Scrims](../bot/scrims.md)), rounds per day, group size |
| Rules | Required mentions, duplicate rules, autodelete settings, DM verification, registration type |
| Role | Success role, open role |

Tier presets 3-tier and above are marked paid — your plan gates which are selectable. The bot-side wizard links here for convenience ("Scrim creation is a piece of cake through dashboard").

## The scrim detail page (`/scrims/[id]`)

Tabs organize the work:

- **Teams** — the registered teams table: slot number, team name, leader, members, status (confirmed / pending / standby). Actions: kick teams (bulk), ban/unban, add a custom team manually, process on-hold registrations.
- **Groups** — the tier groups with their roles/channels; actions to resync groups, send slotlist, send ID pass, open/close screenshot windows.
- **Screenshots** — submissions per group/match: view images, create/edit/delete submissions, and organizer uploads (for entering results from images you received outside Discord).
- **Matches** — schedule matches per group (dialog with map, room details, start time), update or delete them.
- **Standings** — the scrim standings view with publish actions.

<!-- screenshot: dashboard-scrim-detail-teams -->

## Registration control

- **Start registration** / **Stop registration** relay to the bot and toggle the scrim's registration state.
- **Process on-hold** moves waiting registrations to confirmed or standby.
- State changes reflect in Discord within seconds; the scrim's channel messages update accordingly.

## Slot rules

`slot_number` is the canonical identifier. The same rules apply as in Discord: lowest free slot fills next, reserved slots excluded, registration auto-closes at one remaining slot. Dashboard-created registrations follow the same slot pipeline as bot registrations.

## Shuffles

- From the detail page you can trigger a **group shuffle**. Where configured, the dashboard's auto-shuffle service dispatches shuffles automatically when a tier's window passes — scheduled by timer rather than polling, so shuffles fire on time (no missed or delayed rounds) and pending shuffles survive service restarts.
- **Shuffle logs** record every shuffle: mode, score handling, and team movements, for audit.
- Per-tier shuffle configuration is editable on the dashboard.

## Deleting a scrim

Deletion requires confirmation and removes the scrim with its slots, reservations, and bans. Historical result rows survive (they belong to match/player records, not the scrim row).
