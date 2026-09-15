# Dashboard Overview

The web dashboard at `https://tourneyplus.xyz/dashboard` is the browser control center for your events, results, and billing. It mirrors the Discord bot's capabilities and adds billing, quotas, exports, and templates.

<!-- screenshot: dashboard-overview-page -->

## Logging in

1. Open `https://tourneyplus.xyz/dashboard` (or run `/dashboard` in Discord).
2. Sign in **with Discord** (OAuth). You are redirected back to the dashboard after authorizing.
3. Sessions use short-lived access tokens that refresh automatically; logging out ends the session.

You see servers where you hold **Manage Server** (or Administrator). The top bar has:

- **Server selector** — filters all pages to one server, or "All Servers".
- **Game selector** — filters by BGMI / FREEFIRE / VALORANT / CS2.
- **Avatar menu** — My Profile, Settings, Logout.

Servers marked *(Add Bot)* don't have the bot yet; servers marked *(Banned)* or *(Suspended)* are platform-restricted (suspended servers are read-only).

## Navigation

| Section | Page | What it's for |
| --- | --- | --- |
| Main | **Dashboard** | Overview: active events, teams, matches, prize pool, activity feed, charts |
| Main | **Tournaments** | Tournament list, creation (round-plan builder), per-event management |
| Main | **Scrims** | Scrim list, creation, per-scrim teams/groups/screens management |
| Main | **Daily Scrims** | Daily scrim list, creation, per-day management |
| Main | **Matches** | Single-match lobbies: list, creation, per-match management |
| Main | **Billing** | Your servers, plan usage, redeem codes, transaction history |
| Operations | **Results Hub** | Review and process match results across all events |
| Operations | **Custom Forms** | Custom registration forms, entries, import/export |
| Operations | **Verification** | Screenshot verification and tag check setup |
| Operations | **Point Table** | Leaderboard image templates |
| Operations | **Settings** | Per-server bot profile, modlog, autorole, tags, sticky messages, embeds |
| — | **Profile** | Your account, organizer stats, achievements, subscription, and quota usage (avatar menu) |
| — | **Pricing / Payment** | Plan browsing and checkout (also **Upgrade Plan** in the sidebar) |

The top bar carries a **billing summary** (the selected server's plan with recent transactions) next to the avatar menu. An **Admin Panel** section (Dashboard, Server Monitor, User Manager) appears for platform staff.

The dashboard is fully responsive — the sidebar becomes a slide-out menu on phones and tablets, and every page adapts to small screens.

See the [Page Map](page-map.md) for the full route list.

## Dashboard home

The overview page shows, filtered by your server/game selections:

- Primary stat cards: active tournaments, tier scrims, your billing & plan, total teams.
- Secondary stat cards: total matches (all time), peak concurrent players, average match duration, total prize pool across hosted events.
- Charts: matches per day, tier distribution, daily analytics.
- Top performing teams.
- Recent activity log and quick links to create events.

## Server/game filtering

Almost every list page respects the top-bar server and game filters. A filter indicator appears when active. Setting "All Servers" shows cross-server aggregates.

## How actions reach Discord

The dashboard talks to the bot through a real-time bridge. In practice:

- Registration start/stop, group creation, slotlist sends, screenshot windows, and other Discord-side actions are relayed and applied within seconds.
- If the bot is temporarily disconnected, commands are **queued and replayed** when it reconnects — you don't need to retry.
- The health of the bridge is monitored; if an action is stuck, refresh and check the event's state before retrying.

## Permissions on the dashboard

- **Server management pages** require Discord **Manage Server** on the selected server.
- **Event pages** additionally accept the event's mod role (`scrims-mod`, `tourney-mod`, `single-match-mod`) — managers pass automatically.
- **Verification** (ssverify/tagcheck) and **Custom Forms** require Manage Server tier access.
- Role checks are cached briefly (about 60 seconds); a just-granted role may take a minute to take effect.

## Best practices

- Don't double-click state-changing buttons (Start/Stop Registration); wait for the state update. On tournaments and single matches, registration start/stop opens a confirmation that shows the live counts (confirmed / pending / queued registrations) — review them, then confirm.
- Use **Refresh** when a page looks stale before assuming failure.
- Prefer the dashboard for bulk operations (kicking teams, editing many results) and Discord for live, in-channel operations.
