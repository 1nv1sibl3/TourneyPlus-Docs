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
| Main | **Dashboard** | Overview: active events, teams, upcoming matches, prize pool totals, activity feed, charts |
| Main | **Tournaments** | Tournament list, creation (round-plan builder), per-event management |
| Main | **Scrims** | Scrim list, creation, per-scrim teams/groups/screens management |
| Main | **Matches** | Single-match lobbies: list, creation, per-match management |
| Operations | **Results Hub** | Review and process match results across all events |
| Operations | **Prize Pool** | Prize pool management |
| Operations | **Custom Forms** | Custom registration forms and submission data |
| — | **Daily Scrims** | Daily scrim list and management (linked from Scrims/Messages sections) |
| — | **Verification** | Screenshot verification and tag check setup |
| — | **Point Table** | Leaderboard image templates |
| — | **Settings** | Per-server bot profile, modlog, autorole, tags, sticky messages, embeds |
| — | **Profile** | Your account, subscription, and quota usage |
| — | **Pricing / Payment** | Plan browsing and checkout |

An **Admin Panel** section (Dashboard, Server Monitor, User Manager) appears for platform staff.

See the [Page Map](page-map.md) for the full route list.

## Dashboard home

The overview page shows, filtered by your server/game selections:

- Stat cards: active tournaments, active scrims, upcoming matches, total teams, prize pool.
- Charts: activity over time, match outcomes.
- Recent activity log.
- Quick links to create events.

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

- Don't double-click state-changing buttons (Start/Stop Registration); wait for the state update.
- Use **Refresh** when a page looks stale before assuming failure.
- Prefer the dashboard for bulk operations (kicking teams, editing many results) and Discord for live, in-channel operations.
