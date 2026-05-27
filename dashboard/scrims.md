# Scrims

Scrims are tier-based events for repeated competitive sessions.

## Main Pages

- `/scrims`
- `/scrims/config`
- `/scrims/[id]`
- `/scrims/[id]/view`
- `/scrims/[id]/leaderboard`

## Create Scrim

Typical setup fields:
- Name
- Tier preset / slot count
- Registration channel
- Slot list channel
- Required mentions
- Auto-shuffle (ON/OFF)

If auto-shuffle is OFF, no “next shuffle” reminder card should appear.

## Registration Controls

- Start registration
- Stop registration
- Reopen registration when needed

## Slot and Group Checks

- Slot count should reduce as valid teams register.
- Reserved slots and normal registrations are different.
- Group split should match configured structure.

## Result Flow

- Open screenshot window when match starts.
- Teams submit in the configured channel.

Then:
- **AI-enabled plan**: review parsed result and confirm.
- **No AI plan**: enter results manually.

## Leaderboard Terms

- Kill Point
- Position Point
- Rank
- Total Points (`Kill Point + Position Point`)

## Conflict Warnings

- Duplicate rank: highlighted as conflict.
- Unclear kills/rank: highlighted for review.
- Publish asks confirmation if unresolved warnings exist.