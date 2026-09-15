# Plans, Scopes & Entitlements

How TourneyPlus subscriptions work: plans, scopes, entitlements, and how the Free baseline interacts with paid plans.

## The model

```
Plan ── has ──> Entitlements (feature flags & quotas)
Assignment (plan + user/server + time window) ── grants ──> effective entitlements
```

- A **plan** is a product (Free, Basic, Pro, …) defined by typed entitlement rows.
- An **assignment** binds a plan to a user, a server, or both, for a time window (or lifetime).
- At any moment, your server's **effective entitlements** decide what's allowed.

## Scopes

| Scope | Covers | Example use |
| --- | --- | --- |
| `user` | One user's account, across servers | An organizer who runs events in several communities |
| `server` | One Discord server, for anyone managing it | A community buying features for their server |
| `user_server` | One user's actions within one server | A manager's personal upgrade in a specific community |

Paid entitlements overlay the Free baseline **by scope specificity** (global → user → server → user_server): the more specific value wins, and a paid value always beats the Free base value for the same key.

## The Free plan

Every server falls back to the system-managed **Free** plan (`free_default`), seeded automatically. It forms the lowest entitlement layer — so a server without any paid assignment still has baseline capabilities (for example, one concurrent tournament and the 2-tier scrim preset). Paid assignments stack on top.

## Entitlements

Entitlements are feature keys. The ones users most often encounter:

| Key | Gates |
| --- | --- |
| `event.single_match.create` (+ `event.single_match.create.daily`) | Creating single matches from Discord; the daily quota |
| `event.tournament.create` / `event.scrim.create` / `event.daily_scrim.create` | Event creation per type |
| `event.<type>.max_total` | Maximum simultaneous events of a type |
| `event.<type>.max_slots` | Slot pool capacity per event |
| `event.<type>.match.max_total` | Maximum matches |
| `ai.ss.process` / `social.ss.process` | AI screenshot processing / screenshot verification |
| `discord.manage` | Discord-side event management commands |
| `dashboard.manage` | Dashboard management actions |
| `guild.bot.customize` | Per-server bot branding (`/customize`) |
| `guild.branding.customize` | Custom embed colors/footers |
| `event.scrim.max_tier` | Highest usable scrim tier preset |

A denial message always names what's missing and where to upgrade.

## Trials

Trial plans are time-limited plan assignments with a limited window. They can be constrained **once per user** or **once per server**. Trials behave like active plans for entitlements and quotas.

## Enforcement modes

Enforcement is active by default. During platform incidents support may temporarily relax gating — you may see actions succeed that would normally be gated; usage is still recorded.

## Where to check your plan

- **Discord:** `/premium` shows the selected server's active plan, status, auto-renew, and window.
- **Dashboard:** `/profile` shows assignments, windows, and the server's active plan summary; `/billing` adds your subscribed servers, quota usage, and transaction history.

## Buying and renewing

See [Pricing & Checkout](../dashboard/pricing-checkout.md). New assignments queue after currently active ones on the same scope — buying early never loses you paid time.
