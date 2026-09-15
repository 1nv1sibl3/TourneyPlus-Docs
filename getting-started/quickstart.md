# Quickstart: Run Your First Event

This page walks you through a complete **Single Match** — the fastest event type — from inviting the bot to publishing a leaderboard. Expect roughly 15 minutes. Once you can run one event type, the others follow the same pattern with more options.

## Before you start

- You need **Manage Server** permission in the Discord server (or one of the event mod roles after setup).
- Decide which plan your server is on. Some features (multiple simultaneous tournaments, larger tier presets, AI screenshot processing) require a paid plan. Free servers can still run events — see [Plans, Scopes & Entitlements](../subscriptions/plans-and-scopes.md).

<!-- screenshot: discord-bot-invite -->

## Step 1 — Invite the bot and run setup

1. Invite TourneyPlus to your server using the invite link on the [website](https://tourneyplus.xyz) or the bot's Discord profile. Grant the requested permissions (Administrator is simplest; see [Setup & Permissions](../bot/setup-and-permissions.md) for a minimal set).
2. In any channel, run:
   ```
   /setup
   ```
3. The bot creates four private log channels and four mod roles (one pair per event type). It replies with a summary of what was created or refreshed.

`/setup` is safe to re-run at any time — it repairs or recreates missing channels and roles without duplicating them.

## Step 2 — Create a Single Match

1. Run:
   ```
   /smmanager
   ```
   (aliases: `smm`, `smg`; or `/scrim`-style prefix: `!smmanager`)
2. The **Single Match Manager** panel opens. Click **Create Single Match**.
3. Fill in the settings using the lettered buttons:

| Button | Setting | Notes |
| --- | --- | --- |
| A | Match Name | Max 30 characters |
| B | Reg. Channel | Where teams send registration messages |
| C | Slotlist Channel | Where the slot list is posted |
| D | Success Role | Role granted to registered players |
| E | Req. Mentions | Number of teammates that must be tagged (0–5) |
| F | Slots | Total teams, minimum 2 |
| G | Open Time | When registration opens (IST) |
| H | DM Verification | Optional: teammates must confirm via DM |
| I | Registration Type | `Tag based` (default) or `Team Profile` (button-based) |
| J | Confirm Channel | Optional channel for registration confirmations |
| K | Open Role | Role pinged when registration opens |
| L | Game | BGMI / FREEFIRE / VALORANT / CS2 |

<!-- screenshot: bot-single-match-setup -->

4. Press **Save Single Match** (enabled once the required fields are set).

## Step 3 — Registration

1. When the open time arrives (or you toggle registration manually), the bot posts the registration prompt in your registration channel and pings the open role.
2. Team leaders register by sending a message in the registration channel in the format you configured (typically: team name + tagging the required number of teammates).
3. Each valid registration:
   - Fills the next available slot,
   - Gets a confirmation card in the channel,
   - Is granted the Success Role,
   - Is logged in the private log channel.
4. Registration closes automatically when the last slot fills (for scrims/single match), or when you stop it manually.

For everything that can happen during registration — missing profiles, DM verification, pending registrations, slot rules — see [Registration Flow](../bot/registration-flow.md).

## Step 4 — Groups, room details, and the screenshot window

For a single match, one group is created automatically when registration closes. The group gets its own role and text channel.

1. From the Single Match Manager, click **Group Tools**.
2. Use the buttons to manage the group:
   - **Send ID/Pass** — post room ID / password / map for the match (players can press "Get in Copy Format" on the posted message).
   - **Collect Screenshots** — open the screenshot window. Team leaders can now submit one screenshot in the group channel.
   - **Stop Collecting** — close the window.
   - **Process Images** — send submitted screenshots for AI result processing.
3. Alternatively, do this from the dashboard: open `/matches`, click the match, and use the same controls.

<!-- screenshot: bot-group-tools-panel -->

## Step 5 — Review and publish the leaderboard

1. From Group Tools, click **Publish Leaderboard**.
2. Choose the output format: a standard embed, or a styled **image leaderboard** if your server has a point-table template.
3. Preview, then confirm **Publish**. The leaderboard is posted in the channel.
4. Players can press **Request Review** on the published leaderboard to flag it for moderators — the review request lands in your log channel.

Scoring rules: `Total Points = Placement Points + Kills`. Placement points come from the rank table (1st = 10, 2nd = 6, … 7th–8th = 1, 9+ = 0). See [Leaderboards](../bot/leaderboards.md).

<!-- screenshot: bot-published-leaderboard -->

## Step 6 — After the event

- The event remains listed in the manager and on the dashboard until you delete it.
- Deleting an event removes its slots and registrations, but historical stats are preserved on player profiles.
- `/profile` any player to see their accumulated match/kills history across events.

## Where to go next

- Scale up to a recurring league: [Scrims](../bot/scrims.md)
- Run a multi-round competition: [Tournaments](../bot/tournaments.md)
- Automate registration vetting: [Custom Forms](../dashboard/custom-forms.md), [Screenshot Verification](../dashboard/verification.md)
- Go deeper on billing: [Pricing & Checkout](../dashboard/pricing-checkout.md)
