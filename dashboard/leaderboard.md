# Leaderboard Behavior

This page describes expected leaderboard columns and highlight rules across all event types.

## Standard Columns

- Placement (`#`)
- Slot (assigned slot in current scope/group)
- Team
- Rank (from screenshot)
- Position Point
- Kill Point
- Total Points

Formula:
`Total Points = Position Point + Kill Point`

## Rank-to-Position Mapping (default BGMI flow)

- Rank 1 -> 10
- Rank 2 -> 6
- Rank 3 -> 5
- Rank 4 -> 4
- Rank 5 -> 3
- Rank 6 -> 2
- Rank 7 -> 1
- Rank 8 -> 1
- Rank 9+ -> 0

## Highlight Rules (UI)

- **Red highlight**: rank conflict (e.g., duplicate rank collision)
- **Orange highlight**: kill extraction uncertainty or invalid kill value

Highlight should affect the full row block from rank through points.

## Publish Guard

If red/orange conflicts exist, publish flow should show warning and ask for confirmation before sending.

## Filters You Should Use

- by group (A/B/C...)
- by match number
- combined view (all selected matches)

[IMG: Leaderboard with conflict highlights]