# Overview

This guide explains TourneyPlus from an organizer point of view.

If you are starting fresh, follow this order:
1. Invite bot and run initial setup in Discord.
2. Login to dashboard and connect your server.
3. Create your first event (Scrim, Tournament, or Single Match).
4. Open registration and collect teams.
5. Schedule matches and open screenshot windows.
6. Process results and publish leaderboard.

[IMG: Invite Bot + Dashboard login flow]

## Product Areas

- **Discord Bot**: event operations, registration, slot handling, quick moderation tools.
- **Dashboard**: visual event control, match scheduling, results review, leaderboard publishing.
- **Admin Panel**: platform operations (users, servers, jobs, subscriptions, billing, analytics, email).

## Event Types

- **Scrim (Tier)**: recurring/lobby style flow with tier config.
- **Tournament**: round + group structure, multi-match management.
- **Single Match**: one-match fast event flow.

## Access and Limits

Subscription scope can be user-scoped or server-scoped depending on plan configuration.
If no valid subscription is found, premium actions can be blocked.

## What This Docs Set Does Not Cover

- Internal database schema
- Worker internals
- Private implementation details

Use this as operator documentation for day-to-day usage and training.