# Profile & Activity

Route: `/profile`. Your account, your subscriptions, and your quota usage — filtered to the selected server.

<!-- screenshot: dashboard-profile-page -->

## Account details

- Discord identity (avatar, display name).
- Personal stats: total matches, kills, averages, events and teams played (the same lifetime data as the bot's `/profile`).
- Editable profile fields where applicable.

## Subscription details

The **My Subscription** section lists:

- Your plans and assignments (plan name, code, category, trial flag).
- Per assignment: status, scope type, start and end dates, the server it applies to, and any coupon-provided bonus entitlements.
- The selected server's active plan summary: plan name, price, duration unit, assignment window, and source.

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
