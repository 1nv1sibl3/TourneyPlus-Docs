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
| `/customform` | — | Configure custom registration forms (name/email/phone/tags, role on completion) | Manage Server or an event mod role |
| `/customize` | `profileconfig` | Per-server bot branding: nickname, avatar, banner (`/customize nick`, `/customize avatar`, `/customize banner`) | Administrator + premium entitlement |

### Players and teams

| Command | Aliases | Purpose |
| --- | --- | --- |
| `/profile` | `qprofile` | Show a player's profile and stats; optional `member` argument to view someone else |
| `/team` | — | List your active teams; parent of the subcommands below |
| `/team rename` | — | Rename your registered team (locks once scores exist) |
| `/team transfer` | — | Transfer team leadership to a teammate (locks after scores or a screenshot submission) |
| `/team optout` | — | Withdraw your team from the current scrim week (respects opt-out cutoff) |

### Operations and support

| Command | Aliases | Purpose |
| --- | --- | --- |
| `/ssqueue` | `qqueue`, `queuejobs` | Screenshot/OCR queue status per event; optional event ID argument |
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

Panels time out after 60–120 seconds of inactivity — just re-run the command to get a fresh one. Each event type's panel is documented in its own page: [Scrims](scrims.md), [Tournaments](tournaments.md), [Single Match](single-match.md), [Daily Scrims](daily-scrims.md).

## Prefix and slash parity

Every top-level command works both ways:

- Slash: `/tourney`
- Prefix: `!tourney` (the default prefix; may be changed per deployment)

Hybrid subcommands work the same way: `!team rename 42 Phoenix Legends` equals `/team rename` with `event_id: 42` and `new_name: Phoenix Legends`.

## Command availability by context

Some commands behave differently by context:

- `/premium` shows the selected server's plan when run in a server, and a general pricing pointer in DMs.
- `/stats`, `/embed`, and the event managers are server-only.
- `/profile`, `/team`, `/support`, `/dashboard`, `/policy`, `/premium`, `/bugreport`, and `/featurerequest` work anywhere.

## Subscription gating

Some commands check your subscription before acting. When a plan does not include a feature, the bot replies with a denial message that names the entitlement and where to upgrade — for example, saving single matches from Discord checks `event.single_match.create` (plus a daily quota and a slot-pool capacity limit). See [Plans, Scopes & Entitlements](../subscriptions/plans-and-scopes.md).
