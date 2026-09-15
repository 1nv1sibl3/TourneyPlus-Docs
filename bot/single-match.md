# Single Match

A Single Match is the simplest event: one round, one group, one leaderboard. Use it for one-off matches, tryouts, or showmatches.

Open the manager with `/smmanager` (aliases `smm`, `smg`). Requires `single-match-mod` (or `scrims-mod`) or Manage Server.

Unlike scrims (one per server), you can run **multiple single matches simultaneously** — quota and plan capacity permitting. Saving a new single match from Discord checks:

- Total active single-match capacity (`event.single_match.max_total`)
- The `event.single_match.create` entitlement and its daily quota
- The slot-pool capacity for the requested slot count (`event.single_match.max_slots`)

<!-- screenshot: bot-single-match-manager -->

## The Single Match Manager panel

| Button | What it does |
| --- | --- |
| **Create Single Match** | Starts the setup wizard |
| **Edit Settings** | Opens the editor for an existing match |
| **Start/Stop Registration** | Toggle registration |
| **Group Tools** | Group panel (ID pass, screens, leaderboard) — tier/shuffle buttons are removed for single matches |
| **Reserve Slots** | Hold slots for specific users |
| **Ban/Unban** | Manage banned teams |
| **Manage Slotlist** | Repost/refresh the slot list |
| **Process On-Hold** | Retry pending registrations |
| **Delete Single Match** | Delete the event |

## Creating a single match

| Setting | Notes |
| --- | --- |
| Match Name | Max 30 characters |
| Reg. Channel | Where teams register |
| Slotlist Channel | Where the slot list is posted |
| Success Role | Granted on registration |
| Req. Mentions | Teammates that must be tagged (0–5) |
| Slots | Total teams, minimum 2 |
| Open Time | When registration opens (IST) |
| DM Verification | Require teammate DM confirmation |
| Registration Type | `Tag based` or `Team Profile` |
| Confirm Channel | Optional |
| Open Role | Role pinged when registration opens |
| Game | BGMI / FREEFIRE / VALORANT / CS2 |
| Leader-Only Roles | Dashboard setting: when on, only the team leader receives the group role instead of every member (same option as daily scrims and tournaments) |

Two extra infrastructure buttons appear when editing an existing match:

- **Delete Roles/Channel** — remove the match's group channel and roles.
- **Recreate Infra** — delete and rebuild the group channel/role (useful after permission changes).

The group channel is named `<match-name>-match` and the group role `sm<id>#1 Players`. **Save** enables once reg. channel, slotlist channel, success role, slots, and open time are set.

## Single-match lifecycle

1. **Create** the match (wizard above) or from the dashboard `/matches` page.
2. **Registration** opens at the open time, or toggle it manually. Teams register in the reg. channel (see [Registration Flow](registration-flow.md)).
3. Registration closes automatically when the last slot fills.
4. One group with its own role and channel is created when registration closes.
5. From **Group Tools**: send the slot list, send the **ID/Pass** (room ID/password/map), and **Collect Screenshots** to open the screenshot window.
6. Team leaders submit one screenshot in the group channel; **Process Images** sends them for AI result extraction, or enter results manually via the leaderboard flow.
7. **Leaderboard** → publish. Players can press **Request Review** on the published leaderboard if something looks wrong.
8. Delete the match when finished.

<!-- screenshot: bot-single-match-group-tools -->

## Screenshot rules for single match groups

- Only the **team leader** can submit (others' screenshots are removed with a DM explanation).
- **One screenshot per team** per round — duplicates from teammates are removed.
- Accepted file types: `.png`, `.jpg`, `.jpeg` (or any `image/*` attachment).
- The screenshot window must be **open** (Group Tools → **Collect Screenshots**) for submissions to count.
- Moderators with message-management permissions can post in the channel without being treated as submitters.

See [Screenshot Flow & Results](screenshot-flow.md) for the full pipeline.

## Manual group-role assignment

Organizers can drag the group role onto a member manually — the bot notices immediately, captures the assignment, and records it in the single-match log channel. The capture is resilient to brief database hiccups: it retries automatically for about a minute if the database is momentarily unreachable. If it truly cannot save the assignment, the log channel gets an **Admin Audit FAILED** notice asking you to re-apply the role — a lost assignment is never silent.

## Deleting

Deleting a single match removes its slots and registrations. Player stats and historical results already recorded are preserved on profiles. The dashboard's delete requires confirmation and removes the event from both surfaces.
