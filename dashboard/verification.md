# Verification (ssverify & TagCheck)

Two guild-scoped verification features managed from the dashboard's Verification page (and their Discord commands): **screenshot verification** and **tag check** channels. Both require Discord Manage Server on the selected server.

## Screenshot verification (ssverify)

ssverify gates access to a role by requiring players to submit a set number of valid screenshots in a dedicated channel. Each configuration defines:

| Setting | Meaning |
| --- | --- |
| Channel | Where screenshots are submitted |
| Role | The role granted on verification |
| Required screenshots | How many valid submissions are needed |
| Screenshot type | What is verified: any screenshot, YouTube, Instagram, Loco, Rooter, or a **custom filter** (your own keywords) |
| Page name / page URL | The platform/page being verified (used by the type checks) |
| Allow same screenshots | Whether duplicates (same image hash, same user) count |
| Grant mode | Leader only, or full team (leader picks the teammates after verifying) |

<!-- screenshot: dashboard-verification-ssverify -->

### The player experience

1. A player posts their screenshots (`.png`/`.jpg`/`.jpeg`/`.webp` images) in the configured channel.
2. Non-image posts are deleted with a notice; wrong counts are rejected.
3. Each image is checked by type (e.g. YouTube: the screenshot must match the configured channel's content) and, unless "allow same" is on, by perceptual hash for duplicates.
4. Valid screenshots are counted; the reply embed shows progress (Submitted X/Y).
5. At the required count, the role is granted — in **full-team** mode the leader is prompted to select their teammates, and the role is granted to everyone on confirm.

Holders of `tourney-mod`, `scrims-mod`, or `single-match-mod` are **exempt** from verification entirely.

### Limits and errors

- Rate limits: one submission per 7 seconds per member; ten per 60 seconds per guild. Exceeded limits get a "too fast / many users submitting" reply.
- **"OCR exhausted."** — the provider quota is spent; players are told to report it via `/bugreport`.
- **"Failed to process your screenshots."** — transient failure; retry.

### Gating

The feature requires the `social.ss.process` entitlement and the OCR service to be configured ("Screenshot verification is not configured on this bot" otherwise). Configure via `/ssverify` in Discord or the dashboard Verification page — both edit the same records.

## Tag check channels

Tag check channels are **test channels** where players can dry-run their registration message and see how the bot would parse it — team name, mentioned teammates, mapped IGNs — without saving anything or granting roles.

Configuration per channel:

| Setting | Meaning |
| --- | --- |
| Channel | The channel designated as a test channel |
| Required mentions | The mention count the test validates against (0–10) |

<!-- screenshot: dashboard-verification-tagcheck -->

When a player sends a message in a tag check channel, the bot replies with an embed:

- **Parsed team name** and the extracted mentions.
- Each player's mapped IGN (from the message, their game profile, or their general profile), with the source noted.
- **Format errors** (bad custom format, wrong mention count) and **missing profiles** (players with no IGN anywhere), with pointers to fix them.
- The footer stresses: *This is a test validation. No registration has been saved.*

Multiple test channels can be configured per server. Configure via `/tagcheck` in Discord or the dashboard.

## Where these fit

Use ssverify when your event requires pre-verification (e.g. stream-follow requirements); use tag checks to cut down rejected registrations by letting captains practice their message format. Both run alongside — not instead of — normal event registration.
