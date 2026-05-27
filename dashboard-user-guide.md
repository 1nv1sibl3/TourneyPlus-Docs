# TourneyPlus Dashboard User Guide

Last reviewed: May 27, 2026

## 1. Purpose and Scope

This is a client-facing guide for the TourneyPlus web dashboard.

It explains:

- Where each feature is located
- What each page/button does
- What each key setting changes
- When changes apply

It intentionally excludes backend/internal logic.

[IMG TO BE ADDED: dashboard site map]

---

## 2. Login and First Access

1. Open dashboard login page (`/login`).
2. Click `Sign In` (Discord).
3. After login, land on `/dashboard`.
4. In top bar, select your Discord server (not `All Servers`) before creating events.

[VID TO BE ADDED: login + server select]

---

## 3. Global Navigation

### Left sidebar

Primary:

- `Dashboard`
- `Tournaments`
- `Scrims`
- `Matches`

Operations:

- `Results Hub`
- `Prize Pool`

Account / utility:

- `Upgrade Plan` (hidden on highest tiers)
- `Profile`
- `Invite Bot`
- `Logout`

### Top bar

- Breadcrumb path
- `Home` link
- Server selector (`All Servers`, specific server, status tags like Add Bot/Banned/Suspended)
- Game selector (`BGMI`)
- Server plan/invoice button (opens subscription detail dialog)
- Profile menu (`My Profile`, `Logout`)

[IMG TO BE ADDED: annotated top bar + sidebar]

---

## 4. Dashboard Home (`/dashboard`)

### What you see

- KPI cards: `Active Tournaments`, `Tier Scrims`, `Total Prize Pool`, `Total Teams`
- Secondary cards: `Total Matches`, `Peak Concurrent`, `Avg Match Duration`
- Charts: `Matches per Day`, `Tier Distribution`, `Daily Analytics`
- Panels: `Top Performing Teams`, `Upcoming Events`
- Quick actions:
  - `Manage Tournaments`
  - `Manage Scrims`
  - `Create Single Match`
  - `Results Hub`

### User behavior

- Clicking quick-action cards navigates directly to that module.
- Upcoming events are clickable and open related event pages.

[IMG TO BE ADDED: dashboard home quick actions]

---

## 5. Tournaments Module

## 5.1 Tournaments list (`/tournaments`)

### Buttons and controls

- `Create New Tournament`
- Search input (`Search tournaments...`)
- Status filter:
  - `All Status`
  - `Upcoming`
  - `Live`
  - `Completed`
- Per-card actions:
  - `Manage`
  - Delete icon (trash)

### Behavior

- `Manage` opens `/tournaments/{id}/manage`.
- Delete removes tournament after confirmation.

## 5.2 Create Tournament (`/tournaments/create`)

### Main fields (Basic Details)

- `Tournament Title`
- `Prize Pool`
- `Registration Channel`
- `Slotlist Channel`
- `Success Role ID`
- `Required Mentions`
- `Total Teams`
- `Grouping Limit (Teams Per Group)`
- `Number of Rounds`
- `Reserved Organizer Slots`
- `Round 1 Overflow Strategy`
  - `Balanced Spread (Recommended)`
  - `Create Extra Group`
- Round Plan editor:
  - `Regenerate`
  - `Add Round`
  - Per-round fields: `Round Label`, `Matches/Group`, `Advance/Group`, `Input`, `Groups`, `Next`
  - Remove round (trash)
- `Tournament Start Date`
- `Tournament End Date`
- `Rules`

### Footer buttons

- `Back`
- `Next` (if multiple steps are present)
- `Create Tournament`

### Behavior

- Validation runs before create.
- Tournament is created only after `Create Tournament` succeeds.

[VID TO BE ADDED: create tournament from empty form]

## 5.3 Tournament Manager (`/tournaments/{id}/manage`)

### Header actions

- `Start Registration` / `Stop Registration`
- `Manage Slots`
- `Refresh`

### Tabs

- `Round`
- `Group`
- `Slots`
- `Registrations`
- `Processing`
- `Matches`
- `Leaderboard`
- `Tournament Map`

### Round tab

- Round selector buttons (`Round 1`, `Round 2`, etc.)
- Shuffle section:
  - `Preview Promotion`
  - `Shuffle Round X -> Y`
  - Toggles:
    - `Keep old groups/channels after shuffle`
    - `Confirm early shuffle (allow incomplete matches)`
- `Shuffle History` list

### Group tab

Scope controls:

- Round buttons
- Group buttons
- Match dropdown

Room override fields:

- `Map`
- `Room ID`
- `Room Pass`

Actions:

- `Resync Roles`
- `Send ID/Pass`

### Slots tab

Overview badges include capacity, reserve count, pending/completed/queue state.

Controls include:

- Search (`Search Team / Registration ID`)
- Group filter buttons
- Reserve editor
  - `Reserve Group`
  - `Reserve Slots (...)`
  - `Save Reserve`
- `Add Team` block
- Bulk actions:
  - Remove registrations
  - Ban registrations
  - Unban registrations
- Slot grid row actions:
  - `Kick`
  - `Ban`
  - `Unban` (where applicable)

### Registrations tab

- Team cards by state
- Team detail view and quick actions (`Kick`, `Ban`, `Unban`)

### Processing tab

Actions:

- `Open Screenshots`
- `Close Screenshots`
- `Process Screenshots`
- `Open Leaderboard`

Submission controls:

- `Edit Link` / `Cancel Edit`
- `Save Link`
- `Delete`
- Manual screenshot entry form

### Matches tab

Actions:

- `Schedule Match`
- Per match:
  - `Edit Schedule`
  - `Mark Live`
  - `Mark Completed`
  - `Input Scores`
  - `Send ID/Pass`
  - `Delete Match` (pending matches)
- ID/Pass dispatch fields:
  - `Group`
  - `Room ID`
  - `Room Pass`

Edit dialog:

- `Map`
- `Date`
- `Time`
- `Save Changes`

### Leaderboard tab

Actions:

- `Refresh`
- `Publish Leaderboard`

Capabilities:

- Conflict indicators (duplicate rank / kill mismatch)
- Row-level edit mode
- `Edit`
- `Save Changes`
- `Cancel`

### Tournament Map tab

Configuration:

- `Total Teams`
- `Grouping Limit (Teams per group)`
- `Round Count`
- Per-round map fields

Actions:

- `Regenerate`
- `Save Tournament Map`

Tournament settings panel includes:

- `Title`
- `Required Mentions`
- `Tournament Start`
- `Tournament End`
- `Registration Channel ID`
- `Slotlist Channel ID`
- `Success Role ID`
- `Description`
- `Save Settings`

[VID TO BE ADDED: tournament manager full tab walkthrough]

---

## 6. Scrims Module

## 6.1 Scrims ecosystem page (`/scrims`)

### Header actions

- `Create Scrim` / `Configure Scrims` (depending on existing setup)
- `Organise Group`
- `Shuffle History`
- `Delete Scrim`

### Setup cards

- Tier preset cards (2-tier/3-tier/4-tier/5-tier) with:
  - `Use Preset` (available)
  - `Upgrade` (locked)

### Tier cards (after setup)

Each tier card shows:

- Tier name
- Team count/capacity
- Progress bar
- `Manage` button

### Additional panels

- Next shuffle timer
- Registration pipeline lanes:
  - `Pending`
  - `Completed`
  - `Queue`
- Team details dialog and remove actions

[IMG TO BE ADDED: scrims ecosystem tiers + pipeline]

## 6.2 Scrim Wizard (`/scrims/config`)

3-step flow:

- `Core`
- `Schedule`
- `Advanced`

### Core step

- `Tier Preset`
- `Scrim Name`
- `Required Mentions`
- `Registration Channel`
- `Slotlist Channel`
- `Success Role ID`

### Schedule step

- `Scrim Start (Date/Time)`
- `Shuffle Day`
- `Shuffle Time`
- `Auto Shuffle` ON/OFF toggle
- `Rounds Per Day`
- `Group Size`
- `Opt-out Cutoff (hours)`

### Advanced step

- `Slotlist Start`
- `Required Lines`
- `Rulebook (optional)`
- Toggles:
  - `Team Name Required`
  - `Block Duplicate Team Name`
  - `Autodelete Rejected`
  - `Autodelete Extras`
  - `Allow Duplicate Tags`

Footer buttons:

- `Back`
- `Next`
- `Create Scrim` / `Update Scrim`

### Behavior

- Changes are applied only when final create/update action succeeds.

[VID TO BE ADDED: full scrim wizard setup]

## 6.3 Tier manager (`/scrims/{id}`)

### Header actions

- `Start Registration` / `Stop Registration`
- `Process On Hold`
- `Manage Slots`
- `Refresh`

### Tabs

- `Tier`
- `Group`
- `Slots`
- `Processing`
- `Matches`
- `Leaderboard` (opens dedicated leaderboard page)

### Group tab actions

- `Resync Roles`
- `Send ID/Pass`
- `Open Leaderboard`
- Optional room overrides:
  - `Map`
  - `Room ID`
  - `Room Pass`

### Slots tab actions

- `Send Slotlist`
- Search and group filters
- Add Team form:
  - Team name
  - Tier/group selector
  - Discord IDs
  - Leader ID
  - Missing IGN prompts when required
- Bulk actions:
  - `Remove Teams`
  - `Ban Teams`
  - `Unban Teams`
- Grid row actions:
  - `Kick`
  - `Ban`
  - `Unban`
- Banned teams list + `Unban`

### Processing tab actions

- `Open Screenshots`
- `Close Screenshots`
- `Process Screenshots`
- `Open Results Hub`
- Submission actions:
  - `Edit Link`
  - `Save Link`
  - `Delete`
- Manual screenshot entry:
  - Team select
  - Discord message link
  - `Record screenshot entry`

### Matches tab actions

- `Schedule Match`
- Group filter buttons
- Per-match actions:
  - `Edit Schedule`
  - `Mark Live`
  - `Mark Completed`
  - `Mark Pending`
  - `Send ID/Pass`
  - `Delete Match` (pending)
- Dispatch fields:
  - `Room ID`
  - `Room Pass`

[IMG TO BE ADDED: tier manager tab map]

## 6.4 Scrim leaderboard page (`/scrims/{id}/leaderboard`)

Top actions:

- `Back to Group Tools`
- `Refresh`
- `Publish Leaderboard`

Filters:

- Group filter buttons
- `Match Filter`
- `Date Filter`
- `Day Filter`
- `Apply Filters`

Edit mode:

- `Enable Edit Mode` / `Disable Edit Mode`
- Row actions:
  - `Edit`
  - `Save`
  - `Cancel`
- Editable fields:
  - Team rank
  - Member kills
  - Computed total points/kills are shown

Conflict highlighting:

- Red: duplicate rank conflict
- Orange: kill mismatch conflict

[VID TO BE ADDED: leaderboard filter + edit flow]

---

## 7. Matches Module

## 7.1 Single matches list (`/matches`)

### Controls

- `Create New Match`
- Search (`Search matches...`)
- Status filter:
  - `All`
  - `Open`
  - `Live`
  - `Completed`

Per match card:

- `View Details`
- Delete icon

## 7.2 Create Match modal

### Fields

- `Tournament Title`
- `Prize Pool`
- `Mode`
- `Total Slots` (with live fill indicator)
- `Required Mentions`
- `Registration Channel`
- `Slotlist Channel`
- `Success Role ID`
- `Registration End Date`
- `Match Date`
- `Match Time`

Action:

- `Create Match`

## 7.3 Single Match Manager (`/matches/{id}` and `/matches/{id}/view`)

Tabs:

- `Settings`
- `Group`
- `Registrations`
- `Slot List`
- `Processing`
- `Leaderboard`

### Settings tab

- Core settings fields (`Total Slots`, `Registration Start`, and related fields)
- `Save Settings`
- Registration controls:
  - `Start Registration` / `Stop Registration`
  - `Process On-Hold`
- Infrastructure:
  - `Delete Channel/Role`
  - `Recreate Infrastructure`
- Group tools:
  - `Send Slotlist`
  - `Resync Roles`
  - `Send ID/Pass`
  - `Open Screenshot Channel`
  - `Close Screenshot Channel`

### Group / Registrations / Slot List tabs

- Team list actions:
  - `View Team`
  - `Kick`
  - `Ban`
  - `Unban`
- Add Team block:
  - Team name
  - Member IDs
  - Leader ID
  - Missing IGN prompts
  - `Add to Slot List`
- Bulk actions:
  - `Kick Teams`
  - `Ban Teams`
  - `Unban`
  - `Unban All`

### Processing tab

- `Open Screenshot Channel`
- `Close Screenshot Channel`
- `Process Screenshots`
- Submission actions:
  - `Edit`
  - `Save Link`
  - `Delete`
- Manual screenshot entry

### Leaderboard tab

- `Refresh`
- `Publish Leaderboard`
- Row editing:
  - `Edit`
  - `Save`
  - cancel/exit edit

[IMG TO BE ADDED: single match manager tabs]

---

## 8. Results Hub (`/results`)

### Board layout

Three columns:

- `Pending`
- `Processing / Review`
- `Completed`

Per result card:

- `Open Result`

Top action:

- `Refresh`

## 8.1 Process Result modal

### Status and warning blocks

- Queue + submission state stats
- Conflict summary (submission issues, rank conflicts, kill mismatches)

### Actions

- `Process Screenshots`
- `Mark Completed`

### Submission controls

- `Edit`
- `Save Link`
- `Delete`

### Manual entry

- Team selector
- Discord message link
- `Add Screenshot Submission`

### Leaderboard review

- Row actions:
  - `Edit`
  - `Save`
- Editable values:
  - Placement
  - Kills
  - Points
  - Player kill split

[VID TO BE ADDED: results review from Pending to Completed]

---

## 9. Prize Pool (`/prize-pool`)

### Content

- `Grand Total Pool`
- `Major Tournaments`
- `Daily Matches`
- Activity/performance chart
- Tournament breakdown list
- Daily match breakdown list

This page is primarily analytics/read-only from user perspective.

[IMG TO BE ADDED: prize pool analytics cards]

---

## 10. Profile and Subscription (`/profile`)

### What users can do

- View account identity and Discord profile status
- View effective plan/tier
- View server-specific subscription summary
- View quota usage windows
- Redeem coupon code (`Redeem`)
- Switch quota activity view:
  - `My Usage`
  - `All Users`
- Browse:
  - Activity feed
  - Achievements tab

### Common profile controls

- Coupon input + `Redeem`
- Server quota activity filters
- Plan and assignment summary cards

[IMG TO BE ADDED: profile subscription summary + quota panel]

---

## 11. Settings Route (`/settings`)

`/settings` currently redirects to `/profile`.

---

## 12. Change Timing Reference

Use this to understand when users will see each update.

| Change type | When it applies |
|---|---|
| Search/filter input changes | Immediately in the current view/list. |
| Start/Stop registration buttons | Immediate. |
| Save buttons (`Save Settings`, `Save Tournament Map`, `Save Changes`) | After save success returns. |
| Delete actions | After confirmation + successful delete response. |
| Schedule/Reschedule actions | Visible immediately after successful save and refresh. |
| Process screenshot actions | Job starts immediately; result tables update after processing/refetch. |
| Publish leaderboard actions | Publish is queued immediately; output appears once publish completes. |
| Wizard create/update actions | Applied only after final create/update success. |

---

## 13. Recommended Media Plan

Add media in this order for best onboarding:

1. Login + top bar server selection
2. Scrim wizard (Core -> Schedule -> Advanced)
3. Tournament create flow + round planner
4. Tournament manager tabs overview
5. Tier manager (`/scrims/{id}`) tab walkthrough
6. Single match manager tab walkthrough
7. Results hub processing flow
8. Profile quota/coupon panel

[VID TO BE ADDED: complete dashboard operator journey]
