# Screenshot Flow & Results

How match results travel from a team's screen to your leaderboard: the screenshot window, submission rules, AI processing, and manual entry.

## The screenshot window

For every group (scrim group, tournament round group, single match group, daily scrim group), organizers control a **screenshot window**:

- **Collect Screenshots** / **Stop Collecting** (scrims and single matches) — open and close the window.
- **Collect Screens** / **Stop Screens** (tournaments) — one state-aware button: opens the window when closed, closes it when open.
- Closing the window is usually combined with **Lock Chat** to silence the channel between matches.

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

Accepted submissions get a ✅ reaction and are recorded as submissions with status received.

Multiple images in one message: only the **first** is kept, with an in-channel notice.

Moderators (users with Manage Messages / Administrator / Manage Server, or holding `tourney-mod`, `scrims-mod`, `single-match-mod`, `admin`, `moderator`, or `mod` roles) can post freely without being treated as submitters.

## AI processing (OCR)

The **Process** button in Group Tools (**Process Images** for scrims and single matches, **Process SS** for tournaments) submits captured screenshots as OCR jobs:

1. Each submission becomes an **OCR job** (status: queued → processing → done / partial / failed).
2. The processing service extracts **rank** and **kills** from each image and writes the result rows.
3. Submissions move to processed (or **Needs review** when extraction is uncertain).
4. Results land as match team results with source `ai`.

AI processing is plan-gated (entitlement `ai.ss.process`) and requires the OCR service to be configured. If the OCR quota is exhausted, users see: **"OCR exhausted. Please report this incident via `/bugreport`."**

### How names are matched

The service matches the names read from the screenshot against the roster's registered IGNs. Matching tolerates the usual noise:

- **Bracketed names** — an IGN stored or read as `(name)` or `[name]` still matches its roster entry; clan-tag prefixes like `[TP]Name` are left intact.
- **Case and spacing** differences are ignored.

### Multi-screenshot matches

When several screenshots cover the same match (a lobby split across multiple images), each screenshot only scores the teams actually visible in it — a screenshot processed later never zeroes the results of teams that appeared in an earlier one. Teams the latest screenshot couldn't see are listed by name in the processing log.

### Low-match screenshots

If fewer than half of a roster's players could be matched to a screenshot, the job is flagged instead of committing zeros silently: the event's log channel gets a **low match rate** warning naming how many players matched, asking you to verify the results manually. The dashboard's [Results Hub](../dashboard/results-hub.md) shows the same flag for review. Extraction failures surface as warnings too — you always know when a screenshot couldn't be read, rather than discovering zero scores on the leaderboard.

### Checking queue status

```
/ssqueue                → all events in this server
/ssqueue Phoenix Cup    → one event, by name (or a unique part of it)
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

Submissions whose extraction is uncertain land in the **Needs review** status. On the dashboard Results Hub these are surfaced for review before you publish; resolve them by confirming or correcting the parsed values (or switching to manual entry).

## Result modes by plan

- **Plan includes AI processing** — run the full flow above: open window → submissions → process → review → publish.
- **Plan without AI** — registration, scheduling, and screenshot windows still work (the channel serves as proof/log), but you enter rank and kills manually before publishing.

Either way, the publish step is the same: see [Leaderboards](leaderboards.md).
