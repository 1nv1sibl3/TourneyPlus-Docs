# Tournaments

Tournaments support rounds, groups, and multi-match scoring.

## Main Pages

- `/tournaments`
- `/tournaments/create`
- `/tournaments/[id]`
- `/tournaments/[id]/manage`

## Create Tournament

Recommended order:
1. Set title
2. Set slot count and group structure
3. Set required mentions
4. Set registration/confirm channels
5. Set date and schedule settings

## Registration

- Start registration to open entries.
- Stop registration to lock entries.
- Reopen only when needed.

## Group and Match Scheduling

- Schedule matches per round/group.
- Confirm teams are distributed across groups correctly.
- Avoid duplicate schedules for the same scope.

## Result Flow

- Open screenshot intake for selected match.
- Review results before publishing.

By plan:
- **AI-enabled**: parsed values are available for review.
- **No AI**: enter match results manually.

## Leaderboard

- Filter by group and match
- Use combined view when needed
- Publish to Discord after conflict check

## Scoring

- Position Point from rank
- Kill Point from kills
- Total Points = Position Point + Kill Point