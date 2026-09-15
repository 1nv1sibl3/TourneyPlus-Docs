# Profile & Stats

Every Discord user has a persistent **player profile** that survives across events, teams, and servers. Stats accumulate from every match result recorded anywhere on the platform.

## Viewing a profile

```
/profile             → your profile
/profile @Teammate   → someone else's profile
```

The profile card shows:

| Field | Meaning |
| --- | --- |
| Game Profiles | Your in-game name (and ID) **per game** — one row each for BGMI, FREEFIRE, VALORANT, CS2 |
| Total Matches | Match result rows the player appears in |
| Total Kills / Average Kills | Lifetime kills and per-match average |
| Teams Played / Events Played | Distinct teams and events |
| Active Registrations / Teams Led | Current registrations and teams led |
| Achievements | Earned achievement emblems, "X of 14" |
| Last Recorded / Profile Updated | Recency timestamps |

<!-- screenshot: bot-profile-embed -->

Two buttons sit under the card — **Update IGN** and **Link Dashboard**. Both are usable only by the profile owner.

## Updating your IGN

Press **Update IGN**, pick the game, then enter your in-game name (required) and optionally your in-game ID:

- IGNs are stored **per game** — updating your Valorant name never touches your BGMI roster entries. Older single-IGN profiles keep working; the legacy name serves as the fallback until per-game values are set.
- You cannot change an IGN that differs from the stored one while registered in an active event: *"You cannot change IGN while you are registered in an active event."*
- The same modal flow appears in DMs as **Update Player Profile** when a registration is on hold waiting for your IGN (see [Registration Flow](registration-flow.md)).

Your IGN for an event's game can also be set via a custom form with the team-profile collector, or inline in the registration message itself.

## Linking your dashboard account

**Link Dashboard** opens the website's Discord sign-in — authorize once and your Discord account and dashboard profile are linked, so your web profile shows the same stats and history.

## Achievements

Achievements are earned automatically — there is nothing to claim. The catalog covers hosting (first event, tournament streaks, scrim and daily-scrim milestones, hosting 50 events, hosting three different event types, a full year of organizing) and competing (teams led, tournaments entered, matches played, screenshot verifications, AI-processed results). Each achievement has a bronze, silver, or gold emblem, shown on your profile the moment you qualify.

## How stats accumulate

- Every match result that includes you (as leader or member) adds to your lifetime totals.
- Results are never deleted when events are deleted — historical rows persist.
- The same stats power the dashboard's personal profile page (see [Dashboard: Profile & Activity](../dashboard/profile-activity.md)).

The `/team` command complements your profile with team history: total teams, active teams, and your most-played-with teammates (see [Team Commands](team-commands.md)).
