# Release Checklist

Use this checklist before shipping bot/dashboard updates.

## Core Sync

- [ ] dashboard actions map to bot-side handlers
- [ ] bot-side moderation/state mirrors dashboard expectations
- [ ] no stale command/topic mappings

## Event Flows

- [ ] scrim create -> register -> screenshot -> publish
- [ ] tournament create -> group split -> multi-match -> screenshot -> publish
- [ ] single match full lifecycle validated

## Queue and Results

- [ ] points formula verified (`position + kills`)
- [ ] conflict flags visible in results + leaderboard
- [ ] publish warning shown when conflicts exist

## Subscriptions

- [ ] pricing display fields updated
- [ ] assignment flows tested (user scope + server scope)
- [ ] usage tracker logging visible in profile/admin views

## Admin

- [ ] server moderation actions tested
- [ ] user suspend/ban behavior verified
- [ ] analytics export works
- [ ] email manager send/resend paths tested

## UX

- [ ] loading/disabled states prevent action spam
- [ ] no unreadable text blocks
- [ ] mobile layout checked for key pages

[VIDEO: pre-release QA walkthrough]