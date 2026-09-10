# Profile & Stats

Every Discord user has a persistent **player profile** that survives across events, teams, and servers. Stats accumulate from every match result recorded anywhere on the platform.

## Viewing a profile

```
/profile             → your profile
/profile @Teammate   → someone else's profile
```

The profile embed shows:

| Field | Meaning |
| --- | --- |
| In-Game Name / In-Game ID | The player's IGN (per their default game profile) |
| Total Matches | Match result rows the player appears in |
| Total Kills / Average Kills | Lifetime kills and per-match average |
| Teams Played / Events Played | Distinct teams and events |
| Active Registrations / Teams Led | Current registrations and teams led |
| Last Recorded / Profile Updated | Recency timestamps |

<!-- screenshot: bot-profile-embed -->

## Updating your IGN

Press **Update IGN** on the profile embed to open a modal (max 100 characters; submit empty to clear).

- You cannot change your IGN while registered in an active event: *"You cannot change IGN while you are registered in an active event."*
- Only the profile owner can use the button.
- The same modal appears in DMs as **Update Player Profile** when a registration is on hold waiting for your IGN (see [Registration Flow](registration-flow.md)).

## Per-game profiles

IGNs are stored **per game** (BGMI, FREEFIRE, VALORANT, CS2). Event registration resolves your IGN for the event's game; the profile's default IGN is used as the BGMI fallback. Set your IGN via the profile button, a custom form with the team-profile collector, or the registration message itself.

## How stats accumulate

- Every match result that includes you (as leader or member) adds to your lifetime totals.
- Results are never deleted when events are deleted — historical rows persist.
- The same stats power the dashboard's personal profile page (see [Dashboard: Profile & Activity](../dashboard/profile-activity.md)).

## Achievements and history

The `/team` command complements your profile with team history: total teams, active teams, and your most-played-with teammates (see [Team Commands](team-commands.md)).
