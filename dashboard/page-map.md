# Page Map

Every route in the dashboard, what it shows, and who can use it.

## Authenticated app

| Route | Page | Purpose |
| --- | --- | --- |
| `/dashboard` | Dashboard home | Overview stats, activity, charts |
| `/tournaments` | Tournaments list | All tournaments for the selected server/game |
| `/tournaments/create` | Create tournament | Wizard with the round-plan builder |
| `/tournaments/[id]` | Tournament detail | Overview, rounds, groups |
| `/tournaments/[id]/manage` | Tournament manage | Registration, teams, groups, leaderboards |
| `/scrims` | Scrims list | All scrims |
| `/scrims/config` | Create/edit scrim | Scrim configuration wizard |
| `/scrims/[id]` | Scrim detail | Teams, groups, screens, matches |
| `/scrims/[id]/view` | Scrim view | Read-only scrim view |
| `/scrims/[id]/leaderboard` | Scrim leaderboard | Standings and publishing |
| `/daily-scrims` | Daily scrims | Daily scrim list and management |
| `/matches` | Matches | Single-match lobbies: list and creation |
| `/matches/[id]` | Match detail | Single-match management |
| `/matches/[id]/view` | Match view | Read-only match view |
| `/results` | Results Hub | Result review across events |
| `/prize-pool` | Prize Pool | Prize pool management |
| `/custom-forms` | Custom Forms | Form builder and submission data |
| `/verification` | Verification | Screenshot verification and tag check setup |
| `/point-table` | Point Table | Leaderboard image templates |
| `/profile` | Profile | Account, subscription, quota usage |
| `/settings` | Settings | Per-server bot profile, modlog, autorole, tags, sticky, embeds |
| `/pricing` | Pricing | Public plan listing |

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

## Admin panel (platform staff)

| Route | Purpose |
| --- | --- |
| `/admin` | Admin overview |
| `/admin/servers` | Server monitor |
| `/admin/users` | User manager |
| `/admin/subscriptions` | Plans, coupons, assignments, usage, audit |
| `/admin/billing`, `/admin/jobs`, `/admin/features`, `/admin/changelog`, `/admin/email`, `/admin/analytics` | Platform administration |

## Notes

- All authenticated pages respect the top-bar **server** and **game** filters.
- Deeper per-event routes (e.g. a specific group's submissions) hang off the detail pages above and are documented in each feature page.
- API documentation (Swagger) is served at `/docs` for integrators.
