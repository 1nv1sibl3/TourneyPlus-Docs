# Leaderboards

How leaderboards are computed, displayed, and published. This applies to all four event types.

## Scoring

```
Total Points = Placement Points + Kill Points
```

- **Kill Points** = kills (1 point per kill).
- **Placement Points** come from the placement table, which applies to **battle-royale games** (BGMI, FREEFIRE). Non-battle-royale games (VALORANT, CS2) award no placement bonus — kills only.

### Placement table (battle-royale)

| Rank | Placement points |
| --- | --- |
| 1 | 10 |
| 2 | 6 |
| 3 | 5 |
| 4 | 4 |
| 5 | 3 |
| 6 | 2 |
| 7 | 1 |
| 8 | 1 |
| 9+ | 0 |

Points are always recomputed from placement + kills when standings are built, so legacy rows can't skew the totals.

## Sorting

Standings sort by:

1. Total points (descending)
2. Total kills (descending, the tiebreaker)
3. Team name (alphabetical)

## Leaderboard scopes

Depending on the event type, leaderboards can be computed for:

| Scope | Available for |
| --- | --- |
| **Group** | All event types |
| **Round** (cumulative up to a round, or a single round) | Tournaments, scrims |
| **Day** | Scrims, daily scrims |
| **Overall** | All event types |
| **Specific match** (when a group plays multiple matches per round) | Tournaments, scrims |

In the tournament group tools, the **Leaderboard** button asks for `group` or `round` scope, then (if the round has multiple matches per group) a specific match number or `all` for the combined view. Scrim group tools offer **Publish Leaderboard** (group) and **Flexible Leaderboard** (choose round/day/overall).

## Display formats

When publishing, you choose an output format:

- **Embed** — a standard Discord embed listing rank, team (with slot prefix), points, kills, and matches played; includes the most recent match summary and total team count.
- **Image** — a styled leaderboard image rendered from a **point-table template**, when your server has one configured (dashboard → Point Table). Preview mirrors exactly what will be posted.

<!-- screenshot: bot-leaderboard-image-example -->

## Publishing

1. Compute the leaderboard for your chosen scope.
2. A preview is shown (embed or image URL).
3. Confirm **Publish** — the leaderboard is posted to the channel.

Published leaderboards:

- Carry a persistent **Request Review** button. Anyone can press it; the bot posts a review request (with the top-teams snapshot and a message link) into the event's log channel and pings the mod role.
- Are snapshotted into the group's **leaderboard history** (last 20 publishes per group) for audit.

## Manual adjustment after computing

After a leaderboard is computed and shown (tournament group tools), you can opt to **manually set placement/kills** for one team: pick the team by rank number, registration id, or exact name, enter the new values, and a refreshed leaderboard is displayed for publishing.

## The Results Hub and dashboard parity

The dashboard's [Results Hub](../dashboard/results-hub.md) is the review surface for the same data: verify parsed values, correct them, and resolve `needs_review` submissions before publishing. There is no separate "error" concept on publish — a null kills value simply counts as 0 and never blocks publishing.
