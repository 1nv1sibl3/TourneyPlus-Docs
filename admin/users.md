# User Manager

Route: `/admin/users`

## What You Can See

- user profile identity
- active subscriptions
- billing transactions summary
- user moderation state

## Moderation Actions

- **Suspend user**: user can view but action APIs should return blocked state.
- **Ban user**: login/session should show banned notice and block usage.

Apply carefully and keep logs for audit.

## Common Data Expectations

- free plan transactions may still count as billing records
- active subscription count should include valid active assignments

## User Detail Page

Route: `/admin/users/[id]`

Use for deep inspection and manual troubleshooting.

[IMG: User detail panel with moderation actions]