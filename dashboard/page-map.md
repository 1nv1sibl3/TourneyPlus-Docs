# Page Map

Every route in the dashboard, what it shows, and who can use it.

## Authenticated app

| Route | Page | Purpose |
| --- | --- | --- |
| `/dashboard` | Dashboard home | Overview stats, activity, charts |
| `/tournaments` | Tournaments list | All tournaments for the selected server/game |
| `/tournaments/create` | Create tournament | Wizard with the round-plan builder |
| `/tournaments/[id]` | Tournament manage | Registration, teams, groups, leaderboards (the detail route opens manage directly) |
| `/scrims` | Scrims list | All scrims |
| `/scrims/config` | Create/edit scrim | Scrim configuration wizard |
| `/scrims/[id]` | Scrim detail | Teams, groups, screens, matches |
| `/scrims/[id]/view` | Scrim view | Read-only scrim view |
| `/scrims/[id]/leaderboard` | Scrim leaderboard | Standings and publishing |
| `/daily-scrims` | Daily scrims | Daily scrim list and management |
| `/daily-scrims/create` | Create daily scrim | Daily scrim wizard (channels, structure, schedule) |
| `/daily-scrims/[id]` | Daily scrim detail | Slots, days, matches, leaderboard |
| `/matches` | Matches | Single-match lobbies: list and creation |
| `/matches/[id]` | Match detail | Single-match management |
| `/matches/[id]/view` | Match view | Read-only match view |
| `/results` | Results Hub | Result review across events |
| `/custom-forms` | Custom Forms | Form builder, entries grid, import/export |
| `/verification` | Verification | Screenshot verification and tag check setup |
| `/point-table` | Point Table | Leaderboard image templates |
| `/profile` | Profile | Account, organizer stats, achievements, quota usage |
| `/billing` | Billing | Subscribed servers, plan usage, redeem codes, transactions |
| `/settings` | Settings | Per-server bot profile, modlog, autorole, tags, sticky, embeds |
| `/pricing` | Pricing | Public plan listing |

Prize-pool totals live on the dashboard home — there is no separate prize-pool page.

## Auth and checkout

| Route | Purpose |
| --- | --- |
| `/login` | Discord OAuth sign-in |
| `/auth/callback` | OAuth callback |
| `/payment` | Checkout for a selected plan (`?planId=…` or `?planCode=…`; legacy `?tier=…` supported) |

## Public site

| Route | Purpose |
| --- | --- |
| `/` | Landing page |
| `/features` | Feature overview |
| `/changelog` | Public changelog |
| `/about`, `/careers`, `/contact` | Company pages |
| `/terms`, `/privacy`, `/guidelines`, `/license`, `/shipping`, `/cancellation`, `/refund` | Legal and policy pages |
| `/public/tournaments/[id]` | Public tournament view |
| `/share/achievement/[achievementId]/[userId]` | Public achievement share card (linked from the profile's share buttons) |

## Admin panel (platform staff)

| Route | Purpose |
| --- | --- |
| `/admin` | Admin overview |
| `/admin/servers`, `/admin/servers/[guildId]` | Server monitor and per-server detail |
| `/admin/users`, `/admin/users/[id]` | User manager and per-user detail |
| `/admin/subscriptions` (+ `/tracker`) | Plans, coupons, assignments, usage, audit |
| `/admin/billing` | Payment and invoice administration |
| `/admin/events`, `/admin/events/[type]/[id]` | Cross-event monitor and per-event detail |
| `/admin/tournaments`, `/admin/scrims`, `/admin/single-matches`, `/admin/matches` | Per-event-type listings |
| `/admin/achievements` | Achievement definitions and stats |
| `/admin/audit` | Unified audit log |
| `/admin/jobs`, `/admin/features`, `/admin/changelog`, `/admin/email`, `/admin/analytics`, `/admin/team`, `/admin/system`, `/admin/settings` | Platform administration |

## Notes

- All authenticated pages respect the top-bar **server** and **game** filters.
- Deeper per-event routes (e.g. a specific group's submissions) hang off the detail pages above and are documented in each feature page.
