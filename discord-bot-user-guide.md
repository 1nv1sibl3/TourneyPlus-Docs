# TourneyPlus Discord Bot User Guide

Last reviewed: May 27, 2026

## 1. Purpose and Scope

This guide is for server owners, event managers, moderators, and players who use the TourneyPlus Discord bot.

It covers:

- Every user-facing command
- Every major manager panel button
- What each action changes from the user side
- When each change takes effect

It does not include backend/internal implementation details.

[IMG TO BE ADDED: Discord bot command cheat sheet]

---

## 2. Quick Start (Server Admin)

1. Invite the TourneyPlus bot to your Discord server.
2. Run `qsetup` once to create/repair logging + moderation setup.
3. Open the manager you need:
   - Scrims: `smanager` (aliases: `s`, `sm`)
   - Single matches: `smmanager` (aliases: `smm`, `smg`)
   - Tournaments: `tourney` (aliases: `tm`, `t`)
4. Configure channels/roles and start registrations.

[VID TO BE ADDED: first-time setup from `qsetup` to first event]

---

## 3. Command Directory

### Core management commands

| Command | Aliases | What it does |
|---|---|---|
| `qsetup [target] [event_id]` | `setup`, `setuplogs` | Creates or repairs TourneyPlus log channel and mod role setup. |
| `smanager` | `s`, `sm` | Opens Scrim Manager panel. |
| `smmanager` | `smm`, `smg` | Opens Single Match Manager panel. |
| `tourney` | `tm`, `t` | Opens Tournament Manager panel. |
| `ssqueue [event_id]` | `qqueue`, `queuejobs` | Shows screenshot-processing queue status. |

### Profile and player commands

| Command | Aliases | What it does |
|---|---|---|
| `qprofile [@member]` | `profile` | Shows profile card and allows in-game-name update flow. |
| `team` | - | Shows active team participation summary. |
| `team rename [event_id] <new_name>` | - | Renames your registered team (if allowed). |
| `team transfer <@member> [event_id]` | - | Transfers team leadership to another member in same team. |
| `team optout [scrim_id]` | - | Removes your team from current scrim cycle (before cutoff). |

### Support and links

| Command | Aliases | What it does |
|---|---|---|
| `bugreport` | `report`, `bug` | Opens bug report form launcher (`Open Form` button). |
| `featurerequest` | `feature`, `request` | Opens feature request form launcher (`Open Form` button). |
| `support` | `community` | Shows official support server link. |
| `dashboard` | `link` | Shows dashboard URL. |
| `policy` | `policies` | Shows policy links. |
| `premium` | `pricing`, `plans` | Shows plan/pricing info. |

---

## 4. Scrim Manager (`smanager`) - Full Button Reference

Primary panel buttons:

| Button | What it does | When to use |
|---|---|---|
| `Create Scrim` | Starts new scrim creation flow. | First-time setup or new event setup. |
| `Edit Settings` | Opens scrim settings editor. | Change channels, role, mentions, timings, limits. |
| `Instant Start/Stop Reg` | Toggles registration open/closed instantly. | Open or pause intake quickly. |
| `Reserve Slots` | Opens reserved-slot tool. | Pre-lock slots for specific teams/users. |
| `Ban/Unban` | Opens ban controls. | Prevent or restore registrations. |
| `Design` | Opens slotlist design/customization. | Change slotlist look/formatting. |
| `Manage Slotlist` | Slotlist utility menu. | Repost, redesign, or edit slotlist text. |
| `Group Tools` | Opens group operations panel. | Group sync, ID/pass dispatch, screenshot cycle, leaderboard publish. |
| `Process On-Hold` | Processes held registrations. | Move pending/held registrations forward. |

[IMG TO BE ADDED: Scrim Manager home panel]

### Scrim setting/save controls

| Button | What it does |
|---|---|
| `Save Scrim` | Saves edited scrim settings. |
| `Back` | Returns to previous panel without applying new step action. |
| `Delete` | Deletes selected scrim event (if used in delete flow). |

### Registration toggle controls

| Button | What it does |
|---|---|
| `Start Reg` | Opens registrations. |
| `Stop Reg` | Closes registrations. |

### Reserve-slot controls

| Button | What it does |
|---|---|
| `Reserve Slot(s)` | Marks selected slots as reserved. |
| `Remove Reserved` | Removes reservation flag from selected slots. |

### Ban controls

| Button | What it does |
|---|---|
| `Ban Users` | Bans selected users/teams from registration. |
| `Unban Users` | Unbans selected users/teams. |
| `Unban All` | Clears entire ban list for that scope. |

### Slotlist management menu options

| Option | What it does |
|---|---|
| `Repost Slotlist` | Re-sends slotlist message. |
| `Change Design` | Switches slotlist template/design. |
| `Edit Slotlist` | Opens editable slotlist text flow. |
| `Go Back` | Returns to previous manager level. |

### Slotlist design controls

| Button | What it does |
|---|---|
| `Save this design` | Saves current style/template changes. |
| `Reset to default` | Restores default style template. |
| `Exit` | Exits design editor. |

### Group Tools controls (Scrim side)

| Button | What it does |
|---|---|
| `Shuffle Tiers` | Re-shuffles/promotes teams by configured logic. |
| `Organize Groups` | Reorganizes group placement in current scope. |
| `Resync Roles` | Reapplies group roles to current team members. |
| `Leaderboards` | Opens leaderboard tools/views. |
| `Send ID/Pass` | Sends room credentials to scoped teams. |
| `Collect Screenshots` | Opens screenshot collection phase. |
| `Stop Collecting` | Closes screenshot collection phase. |
| `Process Images` | Starts screenshot processing for current scope. |
| `Manual Process` | Manual processing path for non-standard cases. |
| `Publish Leaderboard` | Publishes standings to Discord output. |
| `Adjust Kills` | Opens manual kill adjustments. |
| `Lock Chat` | Locks scoped chat channels. |
| `Unlock Chat` | Unlocks scoped chat channels. |
| `Refresh` | Reloads current data/state. |

[VID TO BE ADDED: complete weekly scrim cycle in Group Tools]

---

## 5. Single Match Manager (`smmanager`) - Full Button Reference

Primary panel buttons:

| Button | What it does |
|---|---|
| `Create Single Match` | Creates one single-match event. |
| `Edit Settings` | Edits event settings and channels/role behavior. |
| `Start/Stop Registration` | Opens/closes registration instantly. |
| `Group Tools` | Opens group utilities for the selected match. |
| `Reserve Slots` | Reserved-slot operations for selected match. |
| `Ban/Unban` | Ban controls for selected match scope. |
| `Manage Slotlist` | Slotlist controls for selected match. |
| `Process On-Hold` | Processes held registrations. |
| `Delete Single Match` | Deletes selected single match. |

Additional single-match controls you may see in editor/tools:

| Button | What it does |
|---|---|
| `Save Single Match` | Saves edited single-match settings. |
| `Delete Roles/Channel` | Removes generated infra (when used). |
| `Recreate Infra` | Recreates required role/channel infra. |
| `Start Reg` | Opens single-match registration. |
| `Stop Reg` | Closes single-match registration. |

[IMG TO BE ADDED: Single Match Manager button map]

---

## 6. Tournament Manager (`tourney`) - Full Button Reference

Primary panel buttons:

| Button | What it does |
|---|---|
| `Create Tournament` | Starts tournament creation flow. |
| `Edit Settings` | Opens tournament settings editor. |
| `Start/Pause Reg` | Toggles tournament registration availability. |
| `Manage Groups` | Opens tournament group tools. |

Tournament group publication/actions:

| Button | What it does |
|---|---|
| `Publish Group List` | Publishes group list to output channel. |
| `Give Roles` | Applies configured group roles to members. |
| `Webhook (Recommended)` | Publishes via webhook flow. |
| `With Bot` | Publishes via bot message flow. |

[VID TO BE ADDED: tournament registration and group publish flow]

---

## 7. Slash Commands (`/scrims ...`)

These are app commands under the `scrims` slash-command group.

### `/scrims create`

Parameters:

- `registration_channel`
- `slotlist_channel`
- `success_role`
- `required_mentions`
- `total_slots`
- `open_time`

What it does: creates a scrim event from slash command directly.

### `/scrims reserve`

Parameters:

- `registration_channel`
- `slot`
- `team_name`
- `user` (optional)
- `expire_time` (optional)

What it does: reserves a slot in a scrim and can optionally fan out to other selected scrims.

### `/scrims unban`

Parameters:

- `user`
- `reason` (optional)

What it does: unbans user from selected scrims where they are currently banned.

### `/scrims slotinfo`

Parameters:

- `user`

What it does: shows where a user currently has slots in server scrims.

### `/scrims slotlist`

Parameters:

- `registration_channel`

What it does: posts slotlist for that scrim to current channel.

[IMG TO BE ADDED: slash command examples]

---

## 8. Team Commands - User Impact and Timing

| Command | Immediate effect | Notes |
|---|---|---|
| `team rename` | Yes, after successful command completion. | Locked if scoring for that team already exists. |
| `team transfer` | Yes, after successful command completion. | Locked if score/submission state already prevents transfer. |
| `team optout` | Yes, immediate removal from current registration. | Respects configured opt-out cutoff window. |

---

## 9. Support Forms (Bug + Feature)

`bugreport` and `featurerequest` open an embed with `Open Form` button.

### Bug form fields

- Bug Title
- What happened?
- Steps to reproduce
- Expected result
- Subscription details (optional)

### Feature form fields

- Feature Title
- What problem does this solve?
- Requested solution
- Impact / Priority
- Extra context (optional)

[IMG TO BE ADDED: support form submission example]

---

## 10. Change Timing Reference (Important)

Use this section to know when a button change is visible.

| Action type | When users see the change |
|---|---|
| Registration toggle (`Start/Stop`) | Immediate. |
| Slot reserve/unreserve | Immediate in slot availability and slotlist behavior. |
| Ban/unban | Immediate for next registration attempts and moderation checks. |
| Settings save (`Save Scrim`, `Save Single Match`, etc.) | After save confirmation; used for next related workflows. |
| Group resync/role sync | Immediate role pass on members currently in scope. |
| Screenshot collect open/close | Immediate channel/process state change. |
| Process screenshots/images | Processing starts immediately; leaderboard updates after processing finishes. |
| Publish leaderboard | Publish job is triggered immediately; message appears after publish completes. |
| Team rename/transfer/optout | Immediate after command success. |

---

## 11. Recommended Media Placement

Add visuals in this order for client onboarding:

1. `qsetup` + first manager open
2. Scrim Manager home and Group Tools
3. Single Match Manager home
4. Tournament Manager home
5. Slash commands examples
6. Bug/Feature form sample

[VID TO BE ADDED: end-to-end "new server to first completed result" journey]
