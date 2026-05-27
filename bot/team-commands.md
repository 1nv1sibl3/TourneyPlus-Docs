# Team Commands

Command group: `team`

## `team rename`

Rename your registered team.

Example:
- `team rename Phoenix Legends`
- `team rename 42 Phoenix Legends`

Restrictions:
- blocked if score records already exist
- name length and sanitization rules apply

## `team transfer`

Transfer team leader to a teammate.

Example:
- `team transfer @NewLeader`
- `team transfer @NewLeader 42`

Restrictions:
- blocked if scores already exist
- blocked if screenshot submission already exists
- new leader must be part of same team

## `team optout`

Opt out team from current scrim window.

Restrictions:
- cutoff time may apply
- only leader/moderator path allowed

## Safety Model

These restrictions protect result integrity once scoring/submission flow starts.

[IMG: Team command response examples]