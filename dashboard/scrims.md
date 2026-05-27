# Scrims

Scrims are tier-driven recurring style events.

## Main Screens

- `/scrims` list and quick actions
- `/scrims/config` creation + advanced configuration
- `/scrims/[id]` event management
- `/scrims/[id]/leaderboard` standings and publish
- `/scrims/[id]/view` summary/detail

[IMG: Scrim list with status cards]

## Create Scrim

Typical inputs:
- Name
- Tier preset / slots
- Registration and slotlist channels
- Required mentions
- Auto-shuffle setting
- Advanced toggles

Notes:
- If auto-shuffle is OFF, no next-shuffle card should appear.
- Multi-register options may be restricted in advanced flow depending on latest UI changes.

## Registration Controls

- Start registration
- Stop registration
- Preserve/reopen behavior depending on state

Best practice:
- Avoid spam-clicking open/close; wait for success response and button state flip.

## Slot and Group Handling

- Slot counts should decrease as valid teams register.
- Reserved slots are tracked separately and should not be confused with fully validated registrations.
- Group distribution should remain consistent with configured structure.

## Screenshot and Results Flow

- Open screenshot window per match/group.
- Teams submit screenshots in designated channel.
- Processing updates leaderboard with rank, kill points, position points, and total points.

## Leaderboard Terms (current wording)

- **Kill Point**
- **Position Point**
- **Rank**
- **Points = Kill Point + Position Point**

## Conflict Handling

- Duplicate rank conflict can be highlighted.
- Uncertain kill extraction can be highlighted.
- Publishing should show warning when unresolved flags exist.

[VIDEO: Scrim full flow from config to leaderboard publish]