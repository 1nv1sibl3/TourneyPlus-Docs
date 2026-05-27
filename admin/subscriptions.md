# Subscription Manager & Tracker

Routes:
- `/admin/subscriptions`
- `/admin/subscriptions/tracker`

## Subscription Manager UI Strategy

For clean UX, split heavy sections into focused pages or drawers:
- Plan creation/editor
- Assignment creation/editor
- Coupon management
- Assignment records

## Plan + Access Rules

Keep editable fields clear and grouped:
- pricing display features (for `/pricing`)
- scope (user/server)
- event quotas
- processing quotas
- game type scope

## Deletion and Archive

- **Archive** for reversible hide.
- **Delete** for permanent cleanup.

Use delete only when plan is truly retired.

## Tracker Page

Should show real usage events, not only derived snapshots.

Views:
- My usage in selected server
- All users usage in selected server

Display format should emphasize:
- by whom
- when
- what was consumed

## Snapshot Cards

Snapshot cards are useful for current hard-limit usage, but event-level history should remain separately visible.

[IMG: Subscription tracker with user/server filter]