# Leaderboard Behavior

This applies to scrim, tournament, and single match leaderboards.

## Columns

- Placement (`#`)
- Slot
- Team
- Rank
- Position Point
- Kill Point
- Total Points

## Formula

`Total Points = Position Point + Kill Point`

## Rank-to-Position Mapping (BGMI)

- Rank 1 -> 10
- Rank 2 -> 6
- Rank 3 -> 5
- Rank 4 -> 4
- Rank 5 -> 3
- Rank 6 -> 2
- Rank 7 -> 1
- Rank 8 -> 1
- Rank 9+ -> 0

## Highlight Rules

- Red row: rank conflict
- Orange row: uncertain/incorrect value

## Publish Rule

When any row is highlighted, publish action warns you and asks for confirmation.

## Filtering Best Practice

Use filters for:
- group (A/B/C...)
- match number
- combined totals