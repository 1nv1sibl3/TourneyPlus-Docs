# Manager Commands

## `smanager`

Purpose: open scrim manager interface.

Usage:
- `smanager`
- `sm`

Requires event manager access + permissions.

## `smmanager`

Purpose: create/manage Single Match events.

Usage:
- `smmanager`
- `smm`

## `tourney`

Purpose: create/manage tournaments.

Usage:
- `tourney`
- `tm`

## `ssqueue`

Purpose: view screenshot queue and processing health.

Usage:
- `ssqueue`
- `ssqueue <event_metadata_id>`

Notes:
- should support pagination for large outputs
- event-level and global queue stats are both relevant

## `qsetup`

Purpose: repair/setup logs and mod roles.

Usage examples:
- `qsetup`
- `qsetup scrim 12`
- `qsetup tourney 4`

## `qprofile`

Purpose: show player profile + usage stats.

Usage:
- `qprofile`
- `qprofile @user`

[VIDEO: manager command quick tour]