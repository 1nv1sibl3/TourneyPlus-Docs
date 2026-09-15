# Team Commands

`/team` shows everything you have ever played in this server on one card — and the buttons on the card manage your active teams. Run it bare in any server channel; there are no subcommands anymore.

## `/team` — your team card

The card lists your team records **five per page**, active registrations first, then history — including teams from events that were later deleted (the event name and type are preserved) and daily-scrim records. At the bottom, a stat grid:

| Field | Meaning |
| --- | --- |
| Total Teams / Active Teams | Every team you led or played on here, and how many are currently active |
| Unique Teammates / Repeated Teammates | How many different players you have played with, and how many more than once |
| Most Played With | Your top recurring teammates, with counts |

If you have no history: *"No team registrations in this server yet. Register in an event's registration channel and your team shows up here."*

<!-- screenshot: bot-team-card -->

The card's buttons:

| Button | What it does |
| --- | --- |
| **Rename** | Rename your active team |
| **Transfer** | Hand over leadership of your active team |
| **Opt Out** | Withdraw your team from the current scrim week |
| **My Form Entries** | Browse your active [custom form](registration-flow.md#custom-forms) entries in this server — as leader or player, with each member's details (your own contact answers only if you are the leader) |

With more than one active registration, a button first asks which team you mean. With none, the management buttons are disabled.

## Renaming a team

- Only the **team leader** or a moderator (Manage Server / event mod role) can rename.
- Name is sanitized to letters, numbers, spaces, `-`, `_`, max **30 characters**.
- **Locked once score records exist**: *"Score records already exist for this team. Team renaming is locked."*
- Renames are logged to the event's log channel with old name, new name, and who did it.

## Transferring leadership

- The new leader **must already be on the same team** — you cannot transfer to an outsider, and bots can't receive leadership.
- Only the team leader (or a moderator) can transfer.
- **Locked once scores exist** or **a screenshot submission exists** for the team:
  - *"Score records already exist for this team. Leadership transfer is locked."*
  - *"A screenshot submission already exists for this team. Leadership transfer is now locked."*
- On success, leadership moves everywhere it matters: the registration record, the slot record, and team member flags. The change is logged.
- Useful when the original leader can't submit the screenshot — transfer first, then submit.

## Opting out

**Opt Out** withdraws your team from the current scrim week:

- Scrim-only. Only the team leader or scrim moderators can opt out.
- Respects the configured **opt-out cutoff**: after the cutoff hour within the current score epoch, *"Opt-out window has closed for this week."*
- The team's registration and slot are **deleted** (the slot is left empty, not backfilled), group roles are removed, and groups are refreshed.
- Success message: *"Your team has opted out and was removed. Slot left empty."*

Moderators can act on any team via the manager panels' slotlist/group tools instead.

## In DMs

Team registrations belong to individual servers, so `/team` in the bot's DMs explains that and points you to the in-server command and the dashboard.
