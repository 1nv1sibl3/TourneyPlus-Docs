# Tournaments

Tournaments support structured rounds/groups with multi-match scheduling.

## Main Screens

- `/tournaments` event list
- `/tournaments/create` creation wizard
- `/tournaments/[id]` overview
- `/tournaments/[id]/manage` operational control panel

[IMG: Tournament manager screen]

## Create Tournament

Recommended setup sequence:
1. Tournament title
2. Slots and group structure
3. Required mentions
4. Registration and confirm channels
5. Dates/window fields used by scheduling flow

Important:
- Keep required mentions aligned with team size policy.
- Use clear channel mapping to avoid cross-event channel conflicts.

## Registration Lifecycle

- Start registration posts the announcement embed.
- Stop registration closes acceptance.
- Re-open should preserve valid registrations unless reset action is chosen.

## Group and Match Scheduling

- Define round/group plan before opening screenshot windows.
- Verify group split after slot fill (A/B/C should distribute correctly).
- Avoid duplicate schedule creation for same round/group/time.

## Screenshot Operations

From manage tools, open screenshot window for target round/group/match.
If dashboard action fails, check channel existence and permissions first.

## Leaderboard and Publish

Leaderboard supports:
- Match-wise or combined scoring (depending on filter scope)
- Group-based filtering
- Publish action to Discord
- Review request flow for moderation

Points model:
- Position Point (from rank)
- Kill Point (from kills)
- Total Points = Position Point + Kill Point

## Conflict and Quality Checks

Before publish, verify:
- No duplicate-rank conflicts unresolved
- No unreadable kill entries left without manual review

[VIDEO: Tournament round/group match scheduling + publish]