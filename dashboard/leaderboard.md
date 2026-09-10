# Leaderboards & Point Tables

Leaderboard behavior shared by all event types, plus the point-table templates that style image leaderboards.

## Scoring

```
Total Points = Placement Points + Kill Points
```

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

Placement points apply to **battle-royale games** (BGMI, FREEFIRE) only; VALORANT and CS2 score kills only. Standings sort by total points, then total kills, then team name.

## Leaderboard display columns

- Placement (`#`)
- Slot
- Team
- Matches played
- Placement / Rank
- Placement points
- Kill points
- Total points

## Filtering and scopes

Leaderboards can be computed per group, per round, per day, per match, or overall. Use the scope selectors on the event's leaderboard page (or answer the prompts in the Discord group tools). For groups with multiple matches per round, choose a specific match number or the combined total.

## Publishing

1. Compute the leaderboard for your scope.
2. Choose the format — **embed** or **image** (when a template exists).
3. Preview (the preview mirrors exactly what will be posted).
4. Publish — posted to the chosen Discord channel with a persistent **Request Review** button; the top-20 snapshot is stored in the group's leaderboard history.

## Point Table templates (`/point-table`)

Point-table templates define the visual styling for image leaderboards:

| Setting | Purpose |
| --- | --- |
| Name | Template identifier |
| Background / accent colors | The image palette |
| Logo | Server or brand logo rendered on the image |
| Title styling | Event/group header formatting |
| Row styling | Rank column, alternating rows, highlight for top finishers |

<!-- screenshot: dashboard-point-table-editor -->

How they're used:

- When publishing from Discord group tools or the dashboard, pick a template and the preview renders the actual image URLs that will be posted.
- Templates are reusable across events; each server typically maintains one or two.
- If no template is chosen, leaderboards publish as standard embeds.

## Review requests

Players can press **Request Review** on any published leaderboard. The request (with top-team snapshot and message link) is posted to the event's log channel with a mod-role ping. Reviews do not modify the leaderboard; organizers correct results and republish.

## History

Each group keeps its last 20 publish snapshots (scope, publisher, entries) — viewable for audit on the event pages.
