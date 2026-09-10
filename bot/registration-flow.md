# Registration Flow

How teams get into your events. This page covers the tag-based and team-profile registration paths, what the bot validates, and what happens when something is missing.

## Opening registration

Registration opens when any of these happens:

- The scheduled **open time** arrives (daily/weekly timer).
- You press **Instant Start/Stop Reg** (or **Start/Pause Reg**) in the manager panel.
- You start it from the dashboard.

When registration opens, the bot:

1. Posts the registration prompt (with your configured open message and design) in the registration channel.
2. Pings the configured **open role** (default `@everyone`).
3. Posts/refreshes the slot list in the slotlist channel.

## How a team registers

### Tag-based (default)

The team leader sends one message in the registration channel containing:

- The **team name** (first quoted text or the message's leading text, per your format),
- **Mentions** of the required number of teammates.

Example for `required_mentions = 3`:

> "Phoenix Legends" @Rider @Shadow @Viper

Players can also include per-player IGNs inline (custom registration format); the parser maps them to the mentioned users.

### Team Profile based

If the event's **Registration Type** is `Team Profile`, message-tagging is ignored. Instead, a persistent **Register** button is posted, and the leader's saved team roster (from custom forms or a guided collector) fills the registration. See [Team Profiles](../dashboard/custom-forms.md) for how rosters are built.

## What the bot validates

In order:

1. **Moderator immunity** — messages from mod-role holders and Manage Server users are ignored (never counted as registrations).
2. **Registration is open** — closed events delete noise messages (subject to the event's autodelete settings).
3. **Slot availability** — with no free slots the message is removed; if standby is enabled the team may be queued.
4. **Custom format parsing** — malformed registrations are rejected with a DM explaining the errors; the message is deleted (or reacted, per settings).
5. **Duplicate rules** — duplicate team names (if `no_duplicate_name`) and multi-registration (if `multiregister` is off) are denied.
6. **Required mentions** — wrong number of tags is rejected.

## Missing IGN handling (profile hold)

Every mentioned player must resolve an **in-game name (IGN)** — from the message, their per-game profile, or their player profile. If a teammate has none:

- If the event does **not** use DM verification, the bot synthesizes a fallback IGN (`DCID_<username>`) and registers normally.
- If DM verification **or** strict IGN checking applies, the registration goes **on hold (pending)**:
  1. The bot DMs each missing member a "Complete Your Player Profile" prompt with an **Update Player Profile** button (a persistent modal asking for the IGN).
  2. The channel gets a notice: *Registration for `TeamName` is on hold until the mentioned players complete their player profiles.*
  3. As soon as every teammate submits their IGN, the registration is **confirmed automatically** and the slot assigned.

If the bot cannot DM a teammate, it says so in the channel and asks them to enable DMs.

## DM verification (dead account check)

When **DM Verification** is enabled, each mentioned teammate receives a DM with **Confirm** / **Decline** buttons:

- **Confirm** — recorded; when all teammates confirm (and profiles are complete) the registration finalizes.
- **Decline** — the leader is notified with the decliner's name; the registration stalls.
- Declined panels and processed registrations show "Registration No Longer Pending" if clicked later.

These DM buttons persist across bot restarts.

## On-hold processing

Registrations stuck on hold (teammate never completed their profile) can be handled by organizers:

- In Discord: manager panel → **Process On-Hold** → choose whether waiting teams move to standby automatically when slots are full. The bot reports: *Confirmed: X • Standby: Y • Still waiting: Z*.
- On the dashboard: the event's teams view has a corresponding on-hold action.

## Slot assignment rules

- `slot_number` is the canonical slot identifier everywhere (bot and dashboard).
- Registrations fill the **lowest available slot number**, so removals don't leave gaps.
- The slot list updates in place as teams are accepted, rejected, or withdrawn.
- **Reserved slots** are excluded from general assignment; reserved users take their reserved slot.
- When one slot remains (scrims, single match), registration closes automatically.

## Withdrawing a team

A team leader can withdraw with `/team optout`:

- Works for scrims (respects the configured opt-out cutoff for the current week — after the cutoff: *"Opt-out window has closed for this week."*).
- Frees the slot, removes group roles, and refreshes groups.
- See [Team Commands](team-commands.md).

## Registration logs

Every accept, reject, and moderation event is logged in the event's private log channel (`tourneyplus-<type>-logs`). Deleted registration messages by the submitting user also free their slot automatically.
