# Profile & Activity

Route: `/profile`. Your account, your achievements as an organizer, your subscriptions, and your quota usage — filtered to the selected server.

<!-- screenshot: dashboard-profile-page -->

## Account details

- Discord identity — avatar and banner on a profile-style header.
- **Connect Discord** — a one-click button that links your Discord account (used for account linking and sign-in).
- Personal stats: total matches, kills, averages, events and teams played (the same lifetime data as the bot's `/profile`).
- Editable profile fields where applicable.

## Organizer stats

A set of stat cards summarizes your history as an organizer:

- **Hosted** — total events you've hosted (all types, all time).
- **Matches** — matches hosted.
- **Organizer score** — a 0–100 rating of your organizing activity.
- Per-type breakdowns — tournaments, scrims, daily scrims, and single matches hosted.

## Achievements

The **Achievements** tab tracks 14 achievements — from first-event milestones (*First Steps*, *Bracket Debut*) through volume milestones (*Tournament Master*, *Scrim Commander*, *Daily Grinder*, *Match Veteran*, *Event Legend*) to versatility and loyalty (*All-Rounder*, *One Year Strong*). Each achievement shows honest progress computed from your real stats, and locked achievements show what's needed to earn them.

Earned achievements can be shared:

- Platform buttons post your **public share page** — a standalone card at `tourneyplus.xyz/share/achievement/…` with a generated image — to X, LinkedIn, WhatsApp, or Instagram.
- Copy the card image, download it, or use your device's native share sheet on mobile.

## Quota history

The **History** tab shows a timeline of your quota consumption — every usage event in chronological order, so you can audit exactly what was consumed, by whom, and when.

## Subscription details

The **My Subscription** section lists:

- Your plans and assignments (plan name, code, category, trial flag).
- Per assignment: status, scope type, start and end dates, the server it applies to, and any coupon-provided bonus entitlements.
- The selected server's active plan summary: plan name, price, duration unit, assignment window, and source.

Billing tasks — redeeming codes, invoices, and per-server plan usage — live on the dashboard's [Billing page](pricing-checkout.md#the-billing-page).

## Server quota activity

Quota views answer "what have we used this period":

| View | Shows |
| --- | --- |
| **Per-server summary** | The selected server's active plan and quota usage rows |
| **Quota usage rows** | Per quota: period (day/week/month/lifetime), window start/end, limit, used, remaining, and whether it's unlimited |
| **Quota events** | The consumption log — who performed which action, when |

Readability tips for the events list — each entry answers three questions: **who** performed the action, **what** was consumed (which quota, how many units), and **when** it happened.

If you see no activity but expect usage:

1. Check the **server selector** — usage is per-server.
2. Check the quota's **window** — daily quotas reset at the UTC day boundary; monthly windows follow the assignment's 28-day cycle anchored to its start.
3. Enforcement may be off platform-wide, in which case actions still log but aren't counted the same way.

## Quota semantics

- `limit = -1` displayed as **unlimited**; `limit = 0` means blocked.
- Monthly periods use 28-day cycles anchored to the assignment start date.
- Lifetime quotas count from the assignment start with no end.

See [Quotas & Usage](../subscriptions/quotas-and-usage.md) for the full model.
