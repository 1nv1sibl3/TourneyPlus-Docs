# Bot Overview & Command Reference

TourneyPlus runs the entire event workflow inside Discord. Most management happens through interactive panels opened by a small set of commands, and everything works both as a slash command and with the message prefix (default `!`).

<!-- screenshot: bot-manager-panel-example -->

## Command reference

### Event managers

| Command | Aliases | Opens | Requires |
| --- | --- | --- | --- |
| `/scrim` | — (also `/smanager`, aliases `s`, `sm`) | Scrims Manager | `scrims-mod` or Manage Server |
| `/smanager` | `s`, `sm` | Scrims Manager (same panel) | `scrims-mod` or Manage Server |
| `/smmanager` | `smm`, `smg` | Single Match Manager | `single-match-mod`, `scrims-mod`, or Manage Server |
| `/tourney` | `tm`, `t` | Tournament Manager | `tourney-mod` or Manage Server |
| `/dailyscrim` | `dscrim`, `dailyscrims`, `ds` | Daily Scrims Manager | `daily-scrims-mod` or Manage Server |

### Setup and configuration

| Command | Aliases | Purpose | Requires |
| --- | --- | --- | --- |
| `/setup` | `qsetup`, `setuplogs` | Create or repair log channels and mod roles for all four event types | Manage Server or any event mod role |
| `/ssverify` | `ss` | Configure screenshot verification for the server | Manage Server or an event mod role |
| `/tagcheck` | — | Configure registration format test channels | Manage Server or an event mod role |
| `/customform` | — | Configure custom registration forms (field builder, team-profile collector, role on completion, entry management, CSV export) — see [Registration Flow](registration-flow.md#custom-forms) | Manage Server or an event mod role |
| `/customize` | `profileconfig` | Per-server bot branding: nickname, avatar, banner (`/customize nick`, `/customize avatar`, `/customize banner`) | Administrator + premium entitlement |

### Players and teams

| Command | Aliases | Purpose |
| --- | --- | --- |
| `/profile` | `qprofile` | Show a player's profile — per-game identities, lifetime stats, achievements; optional `member` argument to view someone else |
| `/team` | — | Your team history in this server on one card (active + past, paginated), with **Rename**, **Transfer**, **Opt Out** and **My Form Entries** buttons — see [Team Commands](team-commands.md) |

### Operations and support

| Command | Aliases | Purpose |
| --- | --- | --- |
| `/ssqueue` | `qqueue`, `queuejobs` | Screenshot/OCR queue status per event; optional event name argument to scope to one event |
| `/embed` | — | Interactive embed builder; optionally edit an existing bot embed by message ID |
| `/bugreport` | `report`, `bug` | Open the bug report form |
| `/featurerequest` | `feature`, `request` | Open the feature request form |
| `/support` | `community` | Support server invite |
| `/dashboard` | `link` | Dashboard link |
| `/policy` | `policies` | Links to Terms, Privacy, Guidelines, Licenses, Shipping, Cancellation, Refund |
| `/premium` | `pricing`, `plans` | This server's active plan details and pricing link |
| `/help` | — | Full command help; `/help <command>` for one command |
| `/ping` | — | Gateway and database latency |
| `/uptime` | — | Bot uptime |
| `/stats` | `botstats`, `status` | Bot, shard, system, and usage statistics |

## How manager panels work

Every manager command opens an interactive panel with buttons. The panel:

- Lists all events of that type in the server (name, slots, game).
- Offers buttons such as **Create**, **Edit Settings**, **Instant Start/Stop Reg**, **Reserve Slots**, **Ban/Unban**, **Design**, **Manage Slotlist**, **Group Tools**, **Process On-Hold**, and **Send Slot Manager**.
- Most buttons open a **selector** (dropdown) asking which event to act on, then a sub-panel.

Panels time out after 60–120 seconds of inactivity — just re-run the command to get a fresh one. Public-facing cards (slot lists, registration confirmations, ID passes, published leaderboards, custom-form panels) use Discord's newer card layout where supported, with automatic fallback to the classic embed — already-posted panels keep working unchanged. Each event type's panel is documented in its own page: [Scrims](scrims.md), [Tournaments](tournaments.md), [Single Match](single-match.md), [Daily Scrims](daily-scrims.md).

## Prefix and slash parity

Every command in this reference works both ways:

- Slash: `/tourney`
- Prefix: `!tourney` (the default prefix; may be changed per deployment)

## Command availability by context

Some commands behave differently by context:

- `/premium` shows the selected server's plan when run in a server, and a general pricing pointer in DMs.
- `/team` in DMs explains that team registrations belong to individual servers and points you to the in-server command.
- `/stats`, `/embed`, `/ssqueue`, and the event managers are server-only.
- `/profile`, `/team`, `/support`, `/dashboard`, `/policy`, `/premium`, `/bugreport`, `/featurerequest`, and `/help` work anywhere, including the bot's DMs.

## Subscription gating

Some commands check your subscription before acting. When a plan does not include a feature, the bot replies with a denial message that names the entitlement and where to upgrade — for example, saving single matches from Discord checks `event.single_match.create` (plus a daily quota and a slot-pool capacity limit). See [Plans, Scopes & Entitlements](../subscriptions/plans-and-scopes.md).
