# Dashboard: Single Match

Managing single-match events from the web. The pages are `/matches` (the single-match lobby list) and `/matches/[id]` (detail). Requires `single-match-mod`, `scrims-mod`, or Discord Manage Server on the selected server.

<!-- screenshot: dashboard-matches-list -->

## The matches list

Cards per single match showing state, slot fill, match time, and map (with per-map styling). Actions: open the detail page, delete (with confirmation). A search/filter bar narrows by state and name. **Create Match** opens a modal to configure a new single match: name, slots, channels, role, required mentions, open time, and game.

## The match detail page

The same management surface as scrims, scoped to the single match:

- **Teams** — registered teams, slot numbers, statuses; kick, ban, manual add.
- **Group** — the single group's role/channel status; resync, send slotlist, send ID pass, open/close screenshot windows.
- **Screenshots** — submissions for the match; create/edit/delete and organizer uploads.
- **Standings** — the single-round standings and publish.

Because a single match has exactly one round and one group, there are no round selectors or shuffle controls — the flow is linear: register → collect → publish.

## Scheduling the match

From the detail page, set the match's start time, map, and room details; they feed the ID pass posted to the group channel. Times are IST.

## Result entry

Both AI and manual flows are supported:

- **AI** — open the screenshot window, let leaders submit in Discord, then process submissions; parsed rank/kills arrive as results.
- **Manual** — open the result rows and type rank and kills per team; or upload organizer-held screenshots and enter values from them.

Either way, publish the leaderboard when the values look right. Null kills count as 0 and never block publishing.

## Notes

- Single-match creation consumes the plan's single-match quota (`event.single_match.create.daily`) and respects total/slot capacity limits.
- Deleting a single match removes its slots and registrations; player stats persist.
- Multiple single matches can run concurrently, quota permitting.
