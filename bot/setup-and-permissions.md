# Setup & Permissions

## Initial Setup

Run:
- `qsetup`

This repairs/creates default log channels + moderator roles for scrim/tournament/single-match flows.

## Permission Baseline

Bot should have:
- Manage Channels
- Manage Roles
- Manage Messages
- Send Messages / Embed Links

## Moderator Access

Typical checks:
- `Manage Server` OR
- event-specific mod role (`scrims-mod`, `tourney-mod`, `single-match-mod`)

## Subscription Enforcement

Even with permissions, actions may be blocked if subscription feature access denies Discord-side event management.

## Persistent Runtime State

After bot restart, registration/runtime state should restore. Startup log should confirm persistent views/state count.

## Role Upgrade/Downgrade Messaging

When organizer roles are granted/revoked, users receive announcement-style messages tagging the affected user.

[IMG: qsetup success embed]