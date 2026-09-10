# Screenshot Flow & Results

How match results travel from a team's screen to your leaderboard: the screenshot window, submission rules, AI processing, and manual entry.

## The screenshot window

For every group (scrim group, tournament round group, single match group, daily scrim group), organizers control a **screenshot window**:

- **Open Screens** — the group channel now accepts screenshot submissions and (typically) is unlocked for the group role to write.
- **Close Screens** — submissions stop; usually combined with **Lock Chat** to silence the channel between matches.

Only submissions while the window is open are captured. The window is scoped to the current match (and round for multi-round events).

## Submitting a screenshot

The **team leader** sends a message with an image attachment in the group channel. The rules, enforced by the bot:

| Rule | Bot behavior on violation |
| --- | --- |
| Only the registered team leader may submit | Message removed; DM: *Only the registered team leader can upload match screenshots.* |
| One screenshot per team per round | Duplicate removed; DM explains and suggests contacting a moderator for a replacement |
| One screenshot per player per round | Duplicate removed with a DM notice |
| File must be `.png`, `.jpg`, or `.jpeg` (or `image/*`) | Message removed; DM explains the accepted formats |
| Team must be confirmed for the group | Message removed; DM: *Your team isn't confirmed for this group yet…* |
| Team must be matched to a registration | Message removed; DM: *I couldn't match you to a confirmed team for this group…* |

Accepted submissions get a ✅ reaction and become **ScreenshotSubmission** records with status `received`.

Multiple images in one message: only the **first** is kept, with an in-channel notice.

Moderators (users with Manage Messages / Administrator / Manage Server, or holding `tourney-mod`, `scrims-mod`, `single-match-mod`, `admin`, `moderator`, or `mod` roles) can post freely without being treated as submitters.

## AI processing (OCR)

**Process Screenshots** / **Process Screens** submits captured screenshots as OCR jobs:

1. Each submission becomes an **OCR job** (status: `queued` → `processing` → `succeeded` / `partial` / `failed`).
2. The processing service extracts **rank** and **kills** from each image and writes the result rows.
3. Submissions move to `processed` (or `needs_review` when extraction is uncertain).
4. Results land as match team results with source `ai`.

AI processing is plan-gated (entitlement `ai.ss.process`) and requires the OCR service to be configured. If the OCR quota is exhausted, users see: **"OCR exhausted. Please report this incident via `/bugreport`."**

### Checking queue status

```
/ssqueue            → all events in this server
/ssqueue 42         → one event metadata ID
```

The output shows, per event: jobs queued/processing/partial/done/failed, and submissions received/processing/review/processed, plus the next pending jobs.

## Manual results

You do not need AI to score matches:

- **Leaderboard → manual adjustment** (group tools): after a leaderboard is computed, you can pick a team (by rank number, registration id, or exact name) and set its placement and kills for the match.
- **Dashboard Results Hub / event pages**: open a result card and edit rank and kills directly; submissions can also be created, edited, or deleted by organizers (including organizer uploads).

Manual rows are recorded with source `manual`. AI-written rows are never silently overwritten by later jobs — a finalized manual result wins.

## Result records

Each result stores:

- **Placement** (rank) and **kills**.
- **Points** — computed as `placement points + kills` (see the table in [Leaderboards](leaderboards.md)).
- **Source** — `manual`, `ai`, or `hybrid` (AI-parsed, then human-adjusted).
- Review state — who reviewed and when; the raw AI payload is kept for audit.

## Conflict review

Submissions whose extraction is uncertain land in `needs_review` status. On the dashboard Results Hub these are surfaced for review before you publish; resolve them by confirming or correcting the parsed values (or switching to manual entry).

## Result modes by plan

- **Plan includes AI processing** — run the full flow above: open window → submissions → process → review → publish.
- **Plan without AI** — registration, scheduling, and screenshot windows still work (the channel serves as proof/log), but you enter rank and kills manually before publishing.

Either way, the publish step is the same: see [Leaderboards](leaderboards.md).
