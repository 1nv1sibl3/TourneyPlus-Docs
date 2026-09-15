# Support Commands

Quick-reference for TourneyPlus's user-facing support commands. All of them work as slash commands and with the prefix, and all of them work in the bot's DMs too.

## `/bugreport`

Aliases: `report`, `bug`.

Opens a button, then a form with fields: Bug Title, What Happened, Steps to Reproduce, Expected Result, and optional Subscription Details. On submit, the report is delivered to the TourneyPlus team's internal bug-report channel and you get:

> Thanks. Your bug report has been submitted to the TourneyPlus team.

## `/featurerequest`

Aliases: `feature`, `request`.

Same flow with fields: Feature Title, What Problem Does This Solve, Requested Solution, Impact / Priority, and optional Extra Context. Delivered to the feature-request channel.

## `/support`

Aliases: `community`.

Posts the official TourneyPlus support server invite. Join it for live help from the team and community.

## `/dashboard`

Aliases: `link`.

Posts the dashboard URL: `https://tourneyplus.xyz/dashboard`.

## `/policy`

Aliases: `policies`.

Posts links to the policy documents: Terms, Privacy, Guidelines, Licenses, Shipping & Delivery, Cancellation, Refund.

## `/premium`

Aliases: `pricing`, `plans`.

Run in a server: shows that server's active plan — plan name, status (Trial/Active), auto-renew, start and end dates (lifetime plans show "Never (lifetime)"), with a link to the pricing page. Run in DMs: general pricing links.

## Other useful commands

| Command | Purpose |
| --- | --- |
| `/ping` | Gateway and database latency |
| `/uptime` | Bot uptime |
| `/stats` | Bot, shard, system, and usage statistics (server-only) |
| `/help` | Command help; `/help <command>` for details on one command |

## When your message can't be posted

If the bot lacks **Send Messages** or **Embed Links** in the channel, support commands fall back to a plain-text notice (or a DM) telling you which permission is missing, rather than failing silently.
