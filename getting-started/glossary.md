# Glossary

## Core Terms

- **Event Metadata ID**: internal event reference used in queue and admin tools.
- **Group**: team bucket (A, B, C...) used for tournament/scrim distribution.
- **Slot**: assigned registration position inside an event/group.
- **Required Mentions**: number of member tags required in registration messages.
- **Leaderboard Publish**: action that sends public leaderboard output to Discord.
- **Results Hub**: dashboard page where submissions are reviewed and corrected.
- **Screenshot Window**: period when teams can submit match screenshots.
- **Queue Job**: backend processing request for screenshot inference.
- **Partial Result**: result where some player fields were unreadable.
- **Conflict**: suspicious or duplicate outcome indicator (e.g., rank collision).

## Status Labels

- **Queued**: waiting for processing.
- **Processing**: currently being handled.
- **Succeeded**: result parsed successfully.
- **Partial**: parsed with uncertainty/errors.
- **Failed**: processing failed or permanently skipped.
- **Needs Review**: manual review required.

## Subscription Terms

- **Server Scope**: subscription tied to one server.
- **User Scope**: subscription tied to the user account.
- **Quota**: usage limits (daily/monthly counters and cap checks).

## Role Terms

- **scrims-mod**: scrim manager role.
- **tourney-mod**: tournament manager role.
- **single-match-mod**: single match manager role.

[IMG: Example status badges and where they appear]