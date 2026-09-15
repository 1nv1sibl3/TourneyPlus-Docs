# Custom Forms

Custom forms collect structured registration data — built-in owner details, teammate tags, and your own custom questions — and assign a role on completion. They are the dashboard-managed counterpart to the bot's `/customform` command, sharing the same configuration.

Manage them at `/custom-forms`. Requires Discord Manage Server on the selected server.

<!-- screenshot: dashboard-custom-forms -->

## What a form is

Each form configuration defines:

| Setting | Meaning |
| --- | --- |
| Target channel | Where the registration form message is posted |
| Role to assign | The role granted on successful completion |
| Game | Which game the team profile is stored under |
| Team size | Minimum and maximum players per team (1–26) |
| Mode | **Custom fields** (full form) or **tag-based** (team name + members only) |
| Embed title / description | The public form message's text |
| Accent color | Tint of the registration panel |
| Thumbnail / banner | Custom images (falls back to the server icon) |
| Team Profile collector | Also collect each player's IGN and UID into an editable team roster |
| Confirmation channel | Where teammates get tagged on submission |
| Submission log channel | Optional channel where every submission is logged for organizers |
| Role scope | Leader only, or all team members |

## The field editor

The editor opens with the standard fields already in place and ready to edit:

- **Owner fields** — Full Name, Email, Phone.
- **Team field** — Team Name.
- **Player fields** — IGN and UID, collected for every teammate.

Add your own fields on top. Each field has a scope (owner, team, or player), a type (text, number, email, phone, URL, dropdown, or long text), a required flag, and optional settings like placeholder and max length.

Two rules keep forms fillable in Discord's popups:

- While the **Team Profile collector is on, Team Name / IGN / UID are locked** — every roster needs them, so they can't be edited or removed there. Turn the collector off to change them.
- **Tag-based mode** drops the custom fields entirely and collects only the team name and members — a lighter flow for simple registrations.

Limits, enforced with clear, actionable errors:

| Limit | Value |
| --- | --- |
| Fields per form | 40 |
| Dropdown options per field | 25 (option labels up to 100 characters) |
| Extra player fields (Team Profiles on) | 3 — the per-player form shows only 5 inputs |
| Team size | 1–26 players (25 teammates plus the leader) |

Removing a field asks for confirmation because its collected answers are stripped from every submission. Forms configured before these limits existed are healed automatically the next time you save them.

<!-- screenshot: dashboard-custom-forms-field-editor -->

## Deploying a form

Saving posts (or edits in place) a persistent registration message in the target channel with a **Register** button. Players click it, fill the form (owner details, teammates, and your custom questions), and on submission:

1. The configured role is granted (leader only or whole team, per Role Scope).
2. Teammates are tagged in the confirmation channel, if set.
3. A **Team Profile** roster is created or updated (when the collector is enabled).
4. The submission is logged — in the submission log channel if one is set.

The same message is kept in sync whether you save from Discord or the dashboard — both surfaces edit the identical configuration and message.

## The entries grid

Clicking a form opens a spreadsheet-like grid: one row per team, one column per field.

<!-- screenshot: dashboard-custom-forms-entries-grid -->

**Sr. No. is canonical everywhere.** Each entry's serial number is computed the same way the bot does it, so Discord's confirmation card, the grid, and exports always agree. Withdrawn entries **keep their number** — an active-only view can therefore show gaps, by design; the next entry simply takes the next number.

Grid features:

- **Search and status filter** — find teams by name; switch between Active, Withdrawn, and all statuses.
- **Inline cell editing** — click any cell to edit that answer. Owner name/email/phone edits are **per-entry overrides**: they're stored on the entry itself, never on the user's saved profile.
- **Per-player editing** — player-scope fields are edited per member in the Members dialog.
- **Members** — add or remove teammates, edit each member's IGN/UID and player fields. The leader is the entry's key and can't be removed (remove the members instead, or withdraw the entry). Rosters must stay within the form's team size and at or above its minimum — a below-minimum save is blocked with an error telling you to add members or withdraw the entry.
- **Withdraw / Restore** — withdrawing soft-deletes the entry (the bot strips its roles); restoring brings it back with the same Sr. No. and data.
- If the bot can't apply a change (it's offline, or lacks permissions), the dashboard tells you instead of failing silently — re-check the team's roles in Discord after fixing the cause.

## Import

The **Import** button opens a wizard that migrates registrations from another bot or a spreadsheet (CSV/XLSX, parsed in your browser):

- **File limits** — up to 10 MB, 5,000 rows, and 100 columns per import.
- **Column mapping** — each column is mapped to an existing field (suggestions are pre-guessed), or can create a new custom field. Auto-created fields count toward the 40-field cap.
- **Surgical updates** — a blank cell never wipes a stored team name or roster, an import never changes an entry's status (withdrawn entries are never resurrected), and a player's linked profile is never created or overwritten by an import.
- **One entry per leader** — re-importing a leader updates their existing entry instead of creating a duplicate.
- **Honest results** — per-row errors are reported and the valid rows still import; an import where every row is rejected writes nothing at all.

## Export

Two exports are available from the entries grid:

- **Export** — downloads the current filtered view (status + search) as XLSX or CSV, Sr. No. included.
- **Per-event CSV** — the selectors above the grid export the registrations of a specific event (a scrim, tournament, single match, or daily scrim).

All CSV exports are hardened against spreadsheet formula injection — they're safe to open directly in Excel or Google Sheets.

## Owner details and privacy

The name/email/phone columns resolve from a user's saved profile **only when that user is a member of the server you're viewing** — an organizer of one server never sees profile data of users who only play elsewhere. Entries whose leader isn't a member (or came from an import) show blank owner details until you fill in a per-entry override.

## Team Profiles

With the collector enabled, each leader owns an editable roster per server per game: team name and members with their IGN/UID. These rosters power **Team Profile registration** on events (the Register-button flow) and auto-fill future form submissions. Rosters live separately from the submission log, so editing a roster never rewrites past submissions.

## Submission data

Every submission is logged append-only with leader, team name, game, members, and collected answers. Even deleting the form preserves registrant data (the log references survive with nulls).

## Saving conflicts

If another organizer edits the form's fields while you have the editor open, your save is **rejected with a conflict error** — *"The form fields were changed elsewhere after you loaded them — reload the form and re-apply your changes."* This protects collected answers: without it, a stale save would silently strip the fields (and their data) the other editor added.

## Editing and maintenance

- Editing a form edits its live message in place.
- **Resend** deletes and re-posts the message (fixes deleted messages or permission changes).
- Deleting a form removes the configuration and its live message, but the submission log is preserved.
- If the target channel is deleted or the bot loses access, saving still records the configuration but the message can't be delivered — fix the channel and use Resend.

## Moderation notes

- The `/customform` bot command opens the same configuration UI in Discord.
- Answer fields are length-limited in the modal (Full Name 150, Email 255, Phone 255 characters) matching the profile columns — oversized answers are rejected client-side.
- Team-profile forms can never skip IGN/UID collection — the locked fields above guarantee every roster is complete.
