# Dashboard Troubleshooting

Symptoms, causes, and fixes for the web dashboard.

## An action didn't take effect

1. **Refresh the page** — list pages cache their last fetch.
2. Wait a few seconds and retry **once** — dashboard actions relay to the bot asynchronously.
3. Confirm you're in the right **server** (top-bar selector) and the right event.
4. If the bot was momentarily disconnected, commands sent meanwhile are queued and replayed automatically — give it a minute before retrying.

## A button is disabled or grayed out

Disabled buttons encode state:

- **Save/Create disabled** — a required field is missing (event wizards gate Save on required fields).
- **Start/Stop Registration disabled** — the event is already in that state.
- **Open/Close Screens disabled** — the screenshot window is already in that state, or no group is selected.
- **Locked round controls** — tournament rounds that were already shuffled are locked from further edits.

If you believe a button should be enabled, refresh first; persistent disablement usually means a permission or plan gate.

## Permission errors

| Situation | Fix |
| --- | --- |
| *You do not have permission…* on a server page | You need Discord **Manage Server** on the selected server (role checks are cached ~60 s — a newly granted role takes a minute) |
| *…requires event access* on an event page | You need the event's mod role (`scrims-mod` / `tourney-mod` / `single-match-mod`) or Manage Server |
| Verification / Custom Forms pages reject you | These require Manage Server tier access specifically — mod roles are not enough |
| Everything fails on one server | The server may be **suspended** (read-only) or **banned** (no access) — the server selector shows the status; contact support |

## Registration button feels stuck

Avoid double-clicking state-changing buttons. Click once and wait for the state to flip; the state reflects the bot's confirmation, which can take a couple of seconds. If genuinely stuck, refresh and check the event in Discord before retrying.

## Screenshot window failed to open

- The group's channel or role was deleted — resync/recreate groups from the event page.
- The bot lacks permissions in the group channel (View/Send/Embed).
- The selected match/group is wrong — verify the scope selectors.

## Leaderboard looks incorrect

- Verify the scoring formula: `placement points + kills` (placement points only for battle-royale games; see [Leaderboards](../bot/leaderboards.md)).
- Check for **Needs review** results in the [Results Hub](results-hub.md).
- Re-open the result rows and confirm values; republish after corrections.
- Remember sorting: points, then kills, then name.

## No quota activity on the profile page

- Verify the **selected server** in the top bar.
- Check the quota **window** — daily windows reset at the UTC day boundary; monthly windows follow the assignment's 28-day cycle.
- Switch between the per-server and personal views.

## Deleting events and shared channels

Before deleting an event that shares its registration/slotlist channels with other events, confirm which event owns which channel. Deleting an event frees its slots and registrations but does not delete shared channels; group channels/roles created specifically for the event should be cleaned up via the event's own controls first (or rely on the delete flow's confirmation).

## Checkout problems

| Symptom | Fix |
| --- | --- |
| *Trial already consumed…* | The trial's once-per limit was used; choose a paid plan. |
| *You do not have permission to purchase this plan for the selected server.* | Select a server you manage, or pick a user-scoped plan. |
| *Payment verification failed.* | Retry checkout; contact support with the transaction id if it persists. |
| Plan didn't activate after payment | Activation runs on the payment webhook; allow a few minutes, then check `/profile`. If still missing, contact support with the payment reference. |

## Custom Forms issues

| Symptom | Explanation / fix |
| --- | --- |
| Sr. No. in the entries grid has gaps (e.g. 1, 2, 5) | Withdrawn entries keep their numbers by design — switch the status filter to **All statuses** to see them. Numbers always match what the bot shows. |
| *"The form fields were changed elsewhere after you loaded them…"* | Another organizer edited the form's fields while you had the editor open. Your save was rejected to protect collected answers — reload the form and re-apply your changes. |
| Import rejected: *"…imports are limited to 100 columns"* / *"…5,000 rows"* | Split the file: remove unused columns or import in batches under 5,000 rows. Files are also limited to 10 MB. |
| Import rejected: *"…limited to 40 total fields on a form"* | The import would auto-create more fields than the 40-field cap allows — map fewer columns to new fields. |
| Can't remove a member from an entry | The leader can't be removed (they're the entry's key) — remove the other members, or withdraw the entry. Saves below the form's minimum team size are blocked: add members or withdraw. |
| An entry's name/email/phone shows blank | Owner details only resolve for users who are members of the server you're viewing. Type a value into the cell to store a per-entry override. |

## Results marked Needs review

An AI-processed screenshot where fewer than half of the expected players matched (blurry, cropped, or wrong image) is flagged **Needs review** instead of committing zeros — open it in the [Results Hub](results-hub.md) and enter the correct values manually.

## Data looks stale or missing

- Events and teams are filtered by the top-bar **server** and **game** selectors — "All Servers" versus one server changes what lists show.
- The bot and dashboard share one database; there is no separate sync step for data. If Discord shows data the dashboard doesn't (or vice versa), refresh; if it persists, report via `/bugreport`.

## When to report a bug

If a page errors out, an action silently fails after a refresh, or data is inconsistent between Discord and the dashboard: run `/bugreport` in Discord with the page, the action, and the approximate time. Check the support server for known incidents first.
