# Server Monitor

Route: `/admin/servers`

## Core Uses

- view connected guilds
- inspect per-server health and metadata
- execute server moderation actions
- disconnect bot from server

## Recommended Behavior

- server list should be visible on initial load without requiring manual expansion clicks.
- action menus should clearly reflect current state (ban/suspend vs unban/unsuspend).

## Actions

- **Disconnect**: bot leaves selected server.
- **Suspend server**: read-only visibility, state-changing operations blocked.
- **Ban server**: full operational block; show banned state immediately when selected.

## Sync Requirement

Server moderation actions must be aligned on both dashboard and bot side.

[IMG: Server monitor action menu]