# Team Commands

Commands for team leaders (and moderators) to manage their registered teams. Parent command: `/team` — running it bare lists your active teams in this server.

## `/team` — your teams

Shows:

- Your active registrations (team name, event, status, your role — Leader or Player — plus round/group tags when set).
- Totals: total teams ever, active teams, unique teammates, repeated teammates.
- **Most played with** — your top 3 recurring teammates.

If you have no history: *"No team history found for you in this server."*

## `/team rename` — rename your team

```
/team rename Phoenix Legends           → renames your (only) active team
/team rename 42 Phoenix Legends        → renames the team in event 42
```

Rules:

- Only the **team leader** or a moderator (Manage Server / event mod role) can rename.
- Name is sanitized to letters, numbers, spaces, `-`, `_`, max **30 characters**.
- **Locked once score records exist**: *"Score records already exist for this team. Team renaming is locked."*
- If you are registered in multiple events and don't give an event ID, the bot lists your options and asks you to re-run with an explicit ID.
- Renames are logged to the event's log channel with old name, new name, and who did it.

## `/team transfer` — hand over leadership

```
/team transfer @NewLeader             → transfer in your (only) active team
/team transfer @NewLeader 42          → transfer the team in event 42
```

Rules:

- The new leader **must already be on the same team** — you cannot transfer to an outsider.
- Bots can't receive leadership.
- **Locked once scores exist** or **a screenshot submission exists** for the team:
  - *"Score records already exist for this team. Leadership transfer is locked."*
  - *"A screenshot submission already exists for this team. Leadership transfer is now locked."*
- On success, leadership moves everywhere it matters: the registration record, the slot record, and team member flags. The change is logged.
- Useful when the original leader can't submit the screenshot — transfer first, then submit.

## `/team optout` — withdraw from the current scrim week

```
/team optout            → withdraw your team from the scrim bound to this channel
/team optout 7          → withdraw from scrim 7
```

Rules:

- Scrim-only. Only the team leader or scrim moderators can opt out.
- Respects the configured **opt-out cutoff**: after the cutoff hour within the current score epoch, *"Opt-out window has closed for this week."*
- The team's registration and slot are **deleted** (the slot is left empty, not backfilled), group roles are removed, and groups are refreshed.
- Success message: *"Your team has opted out and was removed. Slot left empty."*

## Picking the right team automatically

`/team rename` and `/team transfer` resolve your team in this order:

1. An explicit event ID argument, if given.
2. The event bound to the current channel (registration or slotlist channel).
3. Your most recent active registration — but if you have **more than one**, the bot stops and asks for an event ID, listing your options:

> You are registered in multiple events. Re-run with an explicit event ID.
> Example: `team rename <event_id> <new name>`

Moderators can act on any team via the manager panels' slotlist/group tools instead.
