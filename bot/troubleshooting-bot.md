# Bot Troubleshooting

Symptoms, causes, and fixes for the Discord bot. Error messages below are quoted from the bot itself — search this page for the exact text you saw.

## Registration

### Registration is open but entries are not captured

1. Confirm the event's **registration channel** is the channel players are typing in (the manager's edit view shows it).
2. Confirm registration is actually open (green toggle in the manager / dashboard).
3. Confirm the bot has **View Channel**, **Read Message History**, and **Manage Messages** in that channel.
4. Mod-role holders' messages are intentionally ignored — test with a regular member.
5. If the event's registration type is **Team Profile**, tag-based messages are deleted by design; use the Register button.
6. If the server is **banned or suspended** platform-side, the bot stops writing in that guild entirely (contact support).

### "Registration for `TeamName` is on hold until … complete their player profiles"

Expected behavior with DM verification / strict IGN checking. The mentioned teammates must open their DMs and press **Update Player Profile**. Once all submit IGNs, the slot confirms automatically. Stuck registrations can be processed via the manager's **Process On-Hold**.

### "I couldn't DM <@user>. Please enable direct messages…"

The teammate has server DMs disabled. Have them enable DMs ("Allow direct messages from server members") and re-register, or use the fallback flow.

### Slots

- Registrations fill the **lowest free slot number** — a removed team leaves an empty slot, which the next registration takes.
- Reserved slots never fill from general registration.
- Registration auto-closes when one slot remains (scrims/single match).

## Setup and permissions

### "TourneyPlus Setup Incomplete" / "TourneyPlus Setup Failed"

`/setup` could not finish. The message names the failing step and the permission to grant (e.g. *Failed while creating the moderator role. Grant me: Manage Roles, then re-run `setup`*). Grant the permission and re-run `/setup` — completed parts are kept.

### "I could not resolve my own member in this server…"

The bot's member cache is still loading right after a restart. Wait a minute and re-run `/setup`; if it persists, kick and re-invite the bot.

### Role assignment silently fails

The role you're granting (success role, group roles) is **above the bot's highest role**. Move the bot's role up, or the event roles down.

### "You need `scrims-mod` role or `Manage-Server` permissions to use this command."

You lack the required permission for that manager. Ask an admin to grant the mod role (created by `/setup`) or Manage Server.

### "You need `Manage Server` or an event mod role to use this command."

Same, for `ssverify` / `tagcheck` / `customform`. Note `daily-scrims-mod` is **not** accepted by these three commands — only `scrims-mod`, `tourney-mod`, `single-match-mod`.

## Screenshot flow

### Screenshot was removed with a DM

The DM text states the reason. Common cases:

| DM text | Cause |
| --- | --- |
| *Only the registered team leader can upload match screenshots.* | A non-leader submitted. Transfer leadership first with `/team transfer` (before any submission exists). |
| *Your team has already submitted a screenshot for this round.* | One per team per round; ask a moderator to replace it via the dashboard. |
| *A teammate already submitted the screenshot for this round…* | Duplicate from another member. |
| *…did not include a valid screenshot. Please attach a `.png`, `.jpg`, or `.jpeg` file…* | Wrong file type or no attachment. |
| *Your team isn't confirmed for this group yet, so I removed the screenshot.* | Registration still pending/on-hold. |
| *I couldn't match you to a confirmed team for this group…* | You're not registered for this event. |

### "OCR exhausted. Please report this incident via `/bugreport`…"

The processing provider's quota is spent. Report it — the operators will restore capacity. Meanwhile, enter results manually.

### "Failed to process your screenshots. Try again later."

Transient OCR transport failure. Retry; if persistent, use manual results.

### Screenshot submissions aren't counted

The window must be **open** (Group Tools → **Open Screens**), the message must be in the **group channel**, and it must pass the rules above.

## Teams

### "Score records already exist for this team. Team renaming is locked." / "…Leadership transfer is locked."

Renaming and leadership transfer are locked after scoring starts (transfer also locks after any screenshot submission). This is by design to protect result attribution.

### "Opt-out window has closed for this week."

The scrim's opt-out cutoff has passed. The team plays this week or is removed by a moderator.

### "You are registered in multiple events. Re-run with an explicit event ID."

Add the event ID: `team rename 42 NewName` / `team transfer @User 42`.

## Subscription denials

Messages like *"Your subscription does not allow…"*, *"…has reached maximum active single matches"*, or a denial naming a quota mean the server's plan or quota blocks the action:

- Check the active plan with `/premium`.
- See your usage on the dashboard profile page ([Quotas & Usage](../subscriptions/quotas-and-usage.md)).
- Upgrade at the [pricing page](https://tourneyplus.xyz/pricing).

### "You need TourneyPlus Premium to create more than one tournament."

Free servers are limited to one concurrent tournament.

## Slash commands

### A command isn't visible or "the command is disabled in your guild scope"

- Slash commands can take a few minutes to propagate after the bot joins.
- Re-invoking with the prefix (`!`) always works.
- Very large bots sync app commands with some delay; wait and retry.

### Commands feel slow or the bot is unresponsive

- Run `/ping` (gateway + database latency) and `/uptime`.
- If the bot is offline entirely, check the support server's status channel.

## Misc

### Bot posts twice / reacts twice

Report via `/bugreport` with steps — include the event name and rough timestamp.

### Custom embed issues (`/embed`)

- URL fields must start with `http://` or `https://`.
- An embed can hold at most 25 fields and 6000 total characters.
- Only embeds originally sent by the bot can be edited.
