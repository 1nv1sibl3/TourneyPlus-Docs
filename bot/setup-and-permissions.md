# Setup & Permissions

How to get TourneyPlus fully operational in your server, and what each permission is used for.

## Inviting the bot

1. Open the invite link from the [website](https://tourneyplus.xyz) or the bot's profile.
2. Select your server and authorize.

The default invite requests Administrator for simplicity. If you prefer a minimal permission set, grant the bot's role the following server-wide permissions:

| Permission | Why the bot needs it |
| --- | --- |
| Manage Channels | Creating/repairing log channels, group channels, event channels |
| Manage Roles | Creating mod roles, success roles, group roles; granting roles to players |
| Manage Messages | Deleting rejected registration messages, autoclean purges |
| View Channels | Reading registration channels and group channels |
| Send Messages | Registration prompts, slotlists, leaderboards, confirmations |
| Embed Links | Nearly every response is an embed |
| Add Reactions | Registration accepted/rejected reactions |
| Manage Webhooks | The `/embed` webhook-send option |

Channel-level **permission overrides** can deny these per channel. If the bot suddenly stops responding in one channel, check the overrides for its role there.

## Running setup

```
/setup
```

Aliases: `qsetup`, `setuplogs`.

`/setup` creates (or repairs) the default logging infrastructure for **all four event types**:

| Scope | Log channel | Mod role |
| --- | --- | --- |
| Scrim | `tourneyplus-scrims-logs` | `scrims-mod` |
| Tournament | `tourneyplus-tourney-logs` | `tourney-mod` |
| Single Match | `tourneyplus-single-match-logs` | `single-match-mod` |
| Daily Scrim | `tourneyplus-daily-scrims-logs` | `daily-scrims-mod` |

What setup does per scope:

1. Creates the log channel if missing (private — only the mod role and bot can read it).
2. Creates the mod role if missing.
3. Posts and pins a setup note describing the channel's purpose.
4. If any part already exists, it is *refreshed*, not duplicated.

If a step fails (usually missing permissions), the bot replies with exactly which step failed, which permission to grant, and asks you to re-run `/setup`. Completed parts are kept. Example failure message:

> **TourneyPlus Setup Incomplete** — I could not finish creating the default log channels and moderator roles. Fix the permissions listed below and re-run `setup` — parts that already succeeded are kept and will simply be refreshed.
> Scrim: Failed while **creating the moderator role**. Grant me: **Manage Roles**, then re-run `setup`.

## Who can run what

| Capability | Who |
| --- | --- |
| Run `/setup` | Manage Server, or any of `scrims-mod` / `tourney-mod` / `single-match-mod` |
| Manage scrims (`/scrim`, `/smanager`) | `scrims-mod` or Manage Server |
| Manage tournaments (`/tourney`) | `tourney-mod` or Manage Server |
| Manage single matches (`/smmanager`) | `single-match-mod` (also accepts `scrims-mod`) or Manage Server |
| Manage daily scrims (`/dailyscrim`) | `daily-scrims-mod` or Manage Server |
| Configure `ssverify`, `tagcheck`, `customform` | Manage Server or any event mod role (daily-scrims-mod not included) |
| Customize bot branding (`/customize`) | Administrator, plus a subscription entitlement |
| Player commands (`/profile`, `/team …`) | Anyone |
| Screenshot submission | Registered team leaders only |

Notes:

- Mod role holders can **talk in registration channels without being counted as participants** — the bot ignores their messages during registration.
- Screenshot verification holders of any event mod role are exempt from ssverify requirements in that server.

## Role hierarchy

The bot can only grant roles **below its own highest role**. If your success role or group roles sit above the bot's role, role assignment silently fails. Keep the bot's role near the top of the role list, or move your event roles below it.

## Subscription gating

Even with correct Discord permissions, some actions are blocked by your plan:

- Creating more than one tournament in a non-premium server.
- Saving events from Discord when daily quotas are exhausted.
- Screenshot verification when the plan lacks that entitlement, or when the bot's OCR service is not configured.

The denial message always names the reason. See [Plans, Scopes & Entitlements](../subscriptions/plans-and-scopes.md).

## Re-running setup safely

`/setup` is idempotent. Run it:

- After accidentally deleting a log channel or mod role.
- After changing channel permissions that broke logging.
- After re-inviting the bot.

It has a per-server cooldown of 10 seconds.
