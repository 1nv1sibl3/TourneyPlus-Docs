# Single Match

Single Match is a fast one-match event flow.

## Main Screens

- `/matches`
- `/matches/[id]`
- `/matches/[id]/view`

Depending on UI grouping, creation may also be launched from event manager areas.

## Typical Lifecycle

1. Create single match
2. Open registration
3. Fill slots
4. Open screenshot window
5. Process and review result
6. Publish leaderboard

[IMG: Single match event card + actions]

## Scoring

Single match scoreboard should use:
- Rank from screenshot processing
- Position point from rank mapping
- Kill point from extracted kills
- Final points = position point + kill point

If a team has no valid rank and no valid kills, keep it lower than valid submitted teams.

## Edit/Review Expectations

When editing result entries:
- default values should come from processing output (not forced zero)
- manual changes should remain explicit and traceable

## Publish and Review

- Publish sends public leaderboard format.
- Review request option should be available where moderation flow supports it.

[VIDEO: Single match result correction and publish]