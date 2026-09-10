# Results Hub

Route: `/results`. The Results Hub is the review surface for match results across **all** your events — scrims, tournaments, single matches, and daily scrims — filtered by the top-bar server and game selectors.

<!-- screenshot: dashboard-results-hub -->

## What you see

A card per match with results to review:

| Element | Meaning |
| --- | --- |
| Type badge | Event type (scrim / tournament / single match / daily scrim) |
| Status badge | `Pending`, `Processing`, `Review`, `Completed` |
| Event and match name | Which event and match the results belong to |
| Submission counts | Total / Pending / Processing / Processed |

Click **Open Result** to open the processing modal.

## The processing modal

For a selected match, per team:

- View the submitted screenshot.
- Verify or correct the parsed **rank** and **kills**.
- Set the result manually when there is no AI parse.
- Mark the result final.

Edits are recorded with source `manual` (or `hybrid` when you adjust an AI-parsed value), the reviewer, and a timestamp. The original AI payload is kept for audit.

## Plan-based behavior

- **Plan with AI processing** — review parsed values as above.
- **Plan without AI** — the hub is your manual entry surface: type rank and kills per team, then publish from the event's leaderboard page.

## What to verify before publishing

1. Every rank is correct (ranks drive placement points — see [Leaderboards](../bot/leaderboards.md)).
2. Kills are correct (1 point each).
3. `needs_review` submissions are resolved — confirm or fix uncertain parses.
4. Teams with no submitted values sit below teams with values (they show empty rank/kills, contributing 0).

## Notes

- The bot has no concept of a blocking "error" on publish: a null kills value simply counts as 0, and publishing is never hard-blocked by missing data.
- Submissions can also be created, edited, and deleted from each event's detail page (including organizer uploads of screenshots received outside Discord).
- Use `/ssqueue` in Discord for a live queue status check while processing.
