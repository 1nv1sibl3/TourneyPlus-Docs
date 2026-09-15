# Registration Flow & Custom Forms

How teams get into your events. This page covers the tag-based and team-profile registration paths, custom registration forms, what the bot validates, and what happens when something is missing.

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

Example for three required mentions:

> "Phoenix Legends" @Rider @Shadow @Viper

Players can also include per-player IGNs inline (custom registration format); the parser maps them to the mentioned users.

### Team Profile based

If the event's **Registration Type** is `Team Profile`, message-tagging is ignored. Instead, a persistent **Register** button is posted, and the leader's saved team roster (from custom forms or a guided collector) fills the registration. See [Custom forms](#custom-forms) below for how rosters are built.

## What the bot validates

In order:

1. **Moderator immunity** — messages from mod-role holders and Manage Server users are ignored (never counted as registrations).
2. **Registration is open** — closed events delete noise messages (subject to the event's autodelete settings).
3. **Slot availability** — with no free slots the message is removed; if standby is enabled the team may be queued.
4. **Custom format parsing** — malformed registrations are rejected with a DM explaining the errors; the message is deleted (or reacted, per settings).
5. **Duplicate rules** — duplicate team names (when the event's *No Duplicate Name* setting is on) and multi-registration (when *Multi-Register* is off) are denied.
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
- Slot assignment is **atomic**: two registrations submitted at the same moment can never claim the same slot number — one of them simply lands on the next free slot.
- The slot list updates in place as teams are accepted, rejected, or withdrawn.
- **Reserved slots** are excluded from general assignment; reserved users take their reserved slot.
- When one slot remains (scrims, single match), registration closes automatically.

## Withdrawing a team

A team leader can withdraw with the **Opt Out** button on their `/team` card:

- Works for scrims (respects the configured opt-out cutoff for the current week — after the cutoff: *"Opt-out window has closed for this week."*).
- Frees the slot, removes group roles, and refreshes groups.
- See [Team Commands](team-commands.md).

## Custom forms

Custom forms collect structured registration data in a channel with a button-driven flow — team details, player identities, contact info, and anything else you define — and hand out a role on completion. With the **Team Profile Collector** enabled, a completed form also becomes the leader's saved team roster, which registers into `Team Profile` events with one button.

Configure forms with `/customform` (requires Manage Server or an event mod role — `daily-scrims-mod` is not accepted). Forms can also be managed from the [dashboard](../dashboard/custom-forms.md); the two surfaces stay in sync.

<!-- screenshot: bot-customform-picker -->

### The form picker

Running `/customform` opens a card listing every form in the server — each labeled by its **title · registration channel · Form number** — so you always know which form is which. Pick one to manage it, or press **Create New Form**. For an existing form:

| Button | What it does |
| --- | --- |
| **Edit Form** | Re-open the setup wizard |
| **Resend Form** | Post the registration panel in the target channel again |
| **Download Data** | Export entries as CSV — everyone who ever filled the form, or only entries tied to one event. Exports are sanitized so cell values can never execute as spreadsheet formulas |
| **Delete Form** | Two-step confirm; active entries are withdrawn and the form role is removed from members first |

### Building a form — the wizard

The wizard is a grid of lettered buttons (A–N); the embed above them is the legend showing every setting's current value. **Save & Deploy** enables once the target channel and role are set.

| Letter | Setting | Notes |
| --- | --- | --- |
| A | Target Channel | Where the registration panel is posted |
| B | Role to Assign | Role granted on completion |
| C | Team Size | Exact size — 4, 5, or 6 players |
| D | Title | Panel title |
| E | Description | Panel description |
| F | Thumbnail | Panel thumbnail image (defaults to the server icon) |
| G | Banner Image | Panel banner image |
| H | Team Profile Collector | ON: entries become saved team rosters for event registration |
| I | Confirmation Channel | Where public confirmation cards are posted |
| J | Role Scope | `Leader Only` or `All Team Members` |
| K | Fields | Opens the field builder |
| L | Accent Color | Card accent color (defaults to brand) |
| M | Log Channel | Where full-detail entry logs are posted |
| N | Game | BGMI / FREEFIRE / VALORANT / CS2 (dropdown) |

<!-- screenshot: bot-customform-wizard -->

### The field set

New forms open with the standard field set ready to edit: **Owner Details — Full Name, Email, Phone Number** (all required). With the Team Profile Collector ON, **Team Name, IGN and UID** are part of the set — and locked: they are required, cannot be removed, and are always collected per player, because event registration and AI result matching depend on them. With the collector OFF nothing is locked.

From the **Fields** builder you can add extra fields, edit or remove them (locked ones excepted), and reorder them. Fields come in three scopes:

| Scope | Collected |
| --- | --- |
| **Owner** | Once, from the team leader |
| **Team** | Once per entry (e.g. Team Name) |
| **Player** | From every member (e.g. IGN, UID) |

Field types: short text, long text, number, email, phone, URL, and dropdown (up to 25 options). Each field has a label, a required toggle, a placeholder, and a max length. Note that per-player pop-ups hold at most 5 player inputs, so only the first 5 player fields are collected per member — the locked identity fields always make the cut.

### Filling a form — team leaders

The panel posted in the target channel shows the form's title, description and images, a **Requirements** list grouped by scope, and three persistent buttons:

| Button | Who it is for | What it does |
| --- | --- | --- |
| **Verify Team** | Team leader | Start (or re-run) the form |
| **Manage Team** | Leader or member | Open your entry to edit details, leave, or withdraw |
| **Manage (Admin Only)** | Organizers | Open the entry manager (below) |

**Verify Team** opens one form with the leader's own details — prefilled from their player profile, their saved team name for the form's game, and any answers from a previous submission. Next, a panel shows **every player** on the roster with an **Edit** button marked ✓ (complete) or ✗ (missing). The leader can fill in and update every player's details — each pop-up is prefilled from stored records — then confirm.

On submission:

- The configured role is granted (to the leader only, or all members, per **Role Scope**).
- A **public confirmation card** is posted in the confirmation channel: serial number, team name, and member mentions — never the leader's contact details.
- A **full-detail log card** is posted in the log channel for organizers: every answer, including owner contact details and each member's per-player fields.
- **One entry per form per leader is enforced** — a second submission by the same leader cannot create a duplicate. A leader who already holds the form's role is told they have already registered (the entry can then be managed from the form's **Manage Team** button).

<!-- screenshot: bot-customform-confirmation-card -->

Every entry gets a **Sr. No.** (serial number): its position among the form's entries. It is assigned once and never changes — edits, roster changes, and withdrawals never renumber anything.

### Managing entries — organizers

**Manage (Admin Only)** opens a paginated picker over the form's entries (25 per page). Pick one to get the manage panel:

| Action | Notes |
| --- | --- |
| **Edit Entry** | Every answer is editable end-to-end — including each player's details. Required fields may be left empty when an organizer edits someone else's entry (matching the dashboard grid) |
| **Add Member** | Pick users from a member picker, up to the free roster capacity |
| **Kick Member** | Pick and confirm. Blocked when it would drop the team below the form's team size; the leader cannot be kicked |
| **Withdraw Entry** / **Reactivate Entry** | Withdraw removes the entry from the active pool (and the role); withdrawn entries can be restored |

Members manage themselves from **Manage Team**: **Edit My Details** (their own player fields) or **Leave Team** (leaving that empties the roster below the team size withdraws the entry, with a notice).

Every roster change flows through the same pipeline as a fresh submission — roles, the saved team profile, and logs all update — and the entry's Sr. No. never moves.

<!-- screenshot: bot-customform-manage-entry -->

## Registration logs

Every accept, reject, and moderation event is logged in the event's private log channel (`tourneyplus-<type>-logs`). Deleted registration messages by the submitting user also free their slot automatically.
