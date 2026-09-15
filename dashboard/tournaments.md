# Dashboard: Tournaments

Managing tournaments from the web: creation with the round-plan builder, registration, rounds and groups, shuffle, and leaderboards. The page pair is `/tournaments` (list) and `/tournaments/[id]` + `/tournaments/[id]/manage` (detail/management).

Requires the `tourney-mod` role or Discord Manage Server on the selected server.

<!-- screenshot: dashboard-tournaments-list -->

## Creating a tournament (`/tournaments/create`)

A tabbed wizard:

| Tab | Fields |
| --- | --- |
| **Basic details** | Name, description, game, registration channel, confirm channel, success role, required mentions, total slots, teams per group, reserve slots, entry fee, prize pool |
| **Round plan** | Per round: matches per group, advancing teams per group, with a live preview of the resolved structure (group counts per round, team counts, channel caps) |
| **Rules** | Duplicate rules, autodelete rejected (with a delete delay in seconds), DM verification, registration type, open role, success message |

The round-plan preview warns about edge cases (groups that can't divide evenly) and enforces the **250 group-channel cap**. Dates entered are interpreted as IST.

Free servers can keep only one tournament active; the create flow gates additional ones.

<!-- screenshot: dashboard-tournament-create-rounds -->

## The tournament manage page

`/tournaments/[id]` opens the management page directly. Tabs organize the work:

- **Round** — the current round's progress and per-round settings, including the **round shuffle** action (with switches to keep old groups/channels after the shuffle and to allow an early shuffle with incomplete matches).
- **Group** — per-round group management: sync, recreate, role/channel status per group.
- **Slots** — the slot list per group.
- **Registrations** — the teams table with statuses (including whether each team's group role is actually assigned on Discord); manual add, kick, ban.
- **Processing** — screenshot processing for the tournament's matches (manual result entry where AI processing isn't available for the game).
- **Matches** — schedule matches per group.
- **Leaderboard** — standings with publish controls (embed or image format).
- **Tournament Map** — the bracket structure: total teams, teams per group, and the round plan, saved back to the event.

## Registration

**Start/Pause registration** opens a confirmation showing the live counts — confirmed, pending, and queued registrations — and, when stopping, an option to also generate the group channels and roles for the next round. All the registration validation described in [Registration Flow](../bot/registration-flow.md) applies to messages captured by the bot; dashboard-created registrations bypass message validation but follow the slot pipeline.

Settings include the rejection delete delay: when auto-delete of rejected registrations is on, you choose how many seconds a rejected message survives (0 = immediately, blank = the 15-second default, up to 600).

## Rounds and groups workflow

1. Close registration.
2. **Sync groups** for Round 1 — roles and channels are created in Discord.
3. Per group: send slotlist, send ID pass, open screenshot windows, schedule matches.
4. Collect results (screenshots processed by OCR, or manual entry).
5. Publish the round leaderboard.
6. **Round shuffle** — the preview shows promoted/eliminated counts per group, warns on incomplete matches, and asks whether to keep old round channels for history.
7. Repeat for the next round.

The same **Sync Warning** you see in Discord (registrations ahead of group infrastructure) appears here when rounds need recreating.

## Leaderboards

The tournament leaderboard page computes standings for a chosen scope (round, group, match) and lets you publish to Discord in embed or image form. Manual adjustments are applied the same way as from the Discord group tools. See [Leaderboards & Point Tables](leaderboard.md).

## Public tournament view

Tournaments can have a public page at `/public/tournaments/[id]` for sharing brackets and standings outside Discord.
