# Quotas & Usage

How usage limits are counted, reset, and monitored.

## What a quota is

A **quota** is an entitlement with a numeric limit and a period. Example: *"create 5 single matches per day"*. Every gated action:

1. Checks the quota for the current window.
2. Consumes one unit if allowed.
3. Records a usage event (who, what, when).

## Periods and windows

| Period | Window semantics |
| --- | --- |
| **Day** | Resets at the UTC day boundary |
| **Week** | Resets Monday 00:00 UTC |
| **Month** | 28-day cycle anchored to the assignment's start date |
| **Lifetime** | From the assignment start, no end |

The monthly model is why a "monthly" plan is 28 days — quota windows and plan durations use the same cycle.

## Limits

- `limit = -1` — **unlimited**.
- `limit = 0` — blocked.
- Otherwise — max units per window.

Quotas can be marked **hard limit** (enforced) or soft (tracked only).

## Capacity checks (not windowed)

Some limits are *state* checks rather than counted windows — they compare current totals against the plan maximum at action time:

| Check | Example message |
| --- | --- |
| Max simultaneous events of a type | *"Your plan has reached maximum active single matches."* |
| Slot pool per event | *"Your subscription does not allow this single match slot size."* |
| Max matches | Similar, for match creation |

Reducing your event count (deleting or finishing events) immediately frees capacity.

## Viewing usage

On the dashboard **Profile** page (`/profile`):

- **Per-server summary** — the selected server's active plan and quota rows: period, window start/end, limit, used, remaining.
- **Quota events** — the consumption log: who performed each action, what was consumed, and when.

Usage rows are per-server-scoped; switch the top-bar server selector to see another server's usage.

## Reading the numbers

- **Used vs remaining** are per current window. A daily quota at 4/5 has 1 left today; tomorrow it resets.
- **Unlimited** rows never deplete.
- If usage looks missing, check the server selection and the window boundaries (see [Dashboard Troubleshooting](../dashboard/troubleshooting-dashboard.md)).

## Common quota-related denials

| Message | Meaning | Fix |
| --- | --- | --- |
| *…has reached maximum active single matches.* | Concurrent-event cap reached | Delete or finish an event, or upgrade |
| *Your subscription does not allow this single match slot size.* | Slot pool cap | Reduce the event's slot count, or upgrade |
| *Your subscription does not allow saving single matches from Discord.* | Entitlement missing or daily quota spent | Check `/profile`, wait for the window reset, or upgrade |

## Where quotas apply

The main user-visible quotas: event creation (per type, daily), matches, AI screenshot processing, and screenshot verification. Registration itself is not quota-limited — register as many teams as your event has slots.
