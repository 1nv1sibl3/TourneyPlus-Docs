# Tournaments

Tournaments are multi-round competitive events. Teams register once, are split into groups per round, and only advancing teams continue to later rounds until a final leaderboard.

Open the manager with `/tourney` (aliases `tm`, `t`). Requires `tourney-mod` or Manage Server.

<!-- screenshot: bot-tourney-manager-panel -->

## The Tournament Manager panel

| Button | What it does |
| --- | --- |
| **Create Tournament** | Starts the setup wizard |
| **Edit Settings** | Opens the editor for an existing tournament |
| **Start/Pause Reg** | Open or pause registration |
| **Manage Groups** | Opens the round/group tools panel |
| **Send Slot Manager** | Post a persistent slot-manager panel to a channel |

Free servers can create **one tournament at a time**; creating more requires a paid plan.

## Creating a tournament

Click **Create Tournament** and fill the lettered settings:

| Setting | Notes |
| --- | --- |
| Name | Display name |
| Registration Channel | Where teams register |
| Slotlist (Confirm) Channel | Where the slot list is posted |
| Success Role | Granted on registration |
| Required Mentions | Teammates that must be tagged |
| Teams per Group | Group size (minimum 2) |
| Configured Rounds | The round plan: matches per group and advancing teams per group |
| Total Slots | Maximum teams |
| Reserve Slots | Slots held back from general registration |
| Entry Fee / Prize Pool | Informational values shown to players (prize pool management is on the dashboard) |
| Success Message | Custom confirmation message |
| DM Verification | Require teammate DM confirmation |
| Registration Type | `Tag based` or `Team Profile` |
| Confirm Channel | Optional confirmation channel |
| Open Role | Role pinged when registration opens |
| Game | BGMI / FREEFIRE / VALORANT / CS2 |
| Reaction Emojis | Accept/reject reactions |
| Delete Rejected | On: rejected messages are auto-deleted. Off: kept and marked with the reject reaction |

**Save** enables once registration channel, success role, confirm channel, total slots, and teams per group are set.

<!-- screenshot: bot-tourney-setup-wizard -->

## Round plan

The round plan defines each round's structure. For every round you set:

- **Matches per group** — how many matches each group plays in the round.
- **Advancing teams per group** — how many teams from each group move to the next round.

Example: 64 teams, 16 per group, 2 matches per group, 8 advancing → round 2 has 32 teams; repeat until one final round.

The plan is configured in the setup wizard (or the dashboard's create flow, which previews the resolved structure). Group channels per tournament are capped at 250.

## Managing rounds — Group Tools

**Manage Groups** opens the round/group panel. Two selectors at the top scope everything else:

- **Round select** — which round you are operating on. Rounds that have already been shuffled are marked *Locked*.
- **Group select** — which group within the round.

| Button | What it does |
| --- | --- |
| **Sync Groups** | Create/update this round's groups from current registrations (run after closing registration) |
| **Recreate Groups** | Rebuild the round's channels/roles (asks whether to delete the previous round's assets) |
| **Round Shuffle** | Preview and execute the promotion to the next round (promoted vs eliminated shown; warns about incomplete matches; option to keep old round channels for history) |
| **Send Slotlist** | Post the round/group slot list |
| **Send ID Pass** | Post room ID / password / map for the group's next match |
| **Open Screens** / **Close Screens** | Control the group's screenshot window |
| **Process Screens** | Submit collected screenshots for AI processing |
| **Leaderboard** | Compute and publish a leaderboard — group or full-round scope; specific match or combined when multiple matches per group; optional manual placement/kills adjustment afterwards |
| **Resync Roles** | Reconcile group role membership with rosters |
| **Lock Chat** / **Unlock Chat** | Toggle the group channel's write permission for the group role |
| **Shuffle History** | View past round shuffle records |

<!-- screenshot: bot-tourney-group-tools -->

### The Sync Warning

If registrations have advanced to a later round but group channels/roles only exist for earlier rounds, the panel shows a **Sync Warning** telling you to run **Recreate Groups**. This is normal after a shuffle — recreate to materialize the new round's infrastructure.

## Typical tournament run sheet

1. Create the tournament with a round plan.
2. Start registration; teams register (see [Registration Flow](registration-flow.md)).
3. Close registration (manually or automatically when full).
4. **Manage Groups → Sync Groups** — Round 1 groups are created with roles and channels.
5. For each group: **Send Slotlist**, **Send ID Pass**, **Open Screens**.
6. Collect screenshots; **Process Screens**; verify results.
7. **Leaderboard** — publish Round 1 standings.
8. **Round Shuffle** — preview, confirm, optionally keep old round channels.
9. **Recreate/Sync Groups** for Round 2; repeat from step 5.
10. After the final round, publish the final leaderboard.

## Tournament specifics

- Registration can be paused and resumed at any time.
- The editor's slotlist channel doubles as the confirm channel.
- Eliminated teams keep their historical results; player stats accumulate across all events.
- Leaderboards can be published as embeds or styled images when a point-table template exists (see [Leaderboards](leaderboards.md)).

## Managing from the dashboard

Tournament CRUD, round shuffle, group management, and leaderboards are also available at `/tournaments` on the dashboard — see [Dashboard: Tournaments](../dashboard/tournaments.md). The dashboard's create flow includes a visual round-plan builder.
