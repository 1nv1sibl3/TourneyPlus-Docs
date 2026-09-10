# FAQ

Frequently asked questions, grouped by topic.

## General

**Is TourneyPlus free?**
There's a Free baseline plan every server gets automatically. Paid plans add capacity, tier presets, AI screenshot processing, bot customization, and more. See [Plans, Scopes & Entitlements](../subscriptions/plans-and-scopes.md).

**Which games are supported?**
BGMI, FREEFIRE, VALORANT, and CS2. Note: rank-based placement points apply only to the battle-royale games; VALORANT/CS2 score kills only.

**Do I have to use the dashboard?**
No. Everything needed to run events exists in Discord. The dashboard adds billing, bulk operations, result review, exports, and templates — and many people find creation faster there.

**Bot and dashboard disagree about something — which is right?**
Both read the same database, so this indicates a caching delay or a bug. Refresh both; if it persists, `/bugreport` with the event and timestamp.

## Events

**How many events can I run at once?**
One scrim per server (by design). Tournaments: one on Free, more with a paid plan. Single matches: several, subject to your plan's concurrent-event and slot-pool capacity. Daily scrims: subject to plan quotas.

**Registration closed before all slots filled — why?**
Scrims and single matches auto-close when one slot remains. Also check that a moderator didn't stop it, and that the event wasn't full of reserved slots.

**A team registered but the slot says pending.**
Their registration is on hold — a teammate hasn't completed their player profile (or confirmed via DM). Once they do, it confirms automatically; you can also force processing via **Process On-Hold**.

**Can a team change its name or leader mid-event?**
Yes, until scoring starts: `/team rename` and `/team transfer`. Both lock once score records exist (transfer also locks after a screenshot submission exists).

## Results and leaderboards

**The leaderboard shows 0 kills for a team that submitted.**
The submission may still be processing (`/ssqueue` shows the queue), or the result was never entered. Teams without a valid result contribute 0 and rank below teams with values.

**How are ties broken?**
Total points, then total kills, then team name alphabetically.

**Can I re-publish a corrected leaderboard?**
Yes — fix the results (Results Hub or manual adjustment), then publish again. Players can flag issues with the **Request Review** button on the published message.

**Do I need the AI plan to use screenshots?**
No. Without AI, the screenshot channel still works as proof/log; you enter rank and kills manually before publishing.

## Accounts and billing

**Can one subscription cover multiple servers?**
User-scoped plans cover your account across servers; server-scoped plans cover one server. Check a plan's allowed scopes at checkout.

**What happens when my plan expires?**
Entitlements fall back to the Free baseline (for example, bot branding reverts). Your events and historical data are not deleted.

**I paid but the plan isn't showing.**
Activation runs on the payment webhook — allow a few minutes, then check `/profile` (dashboard) or `/premium` (Discord). If still missing, contact support with the payment reference.

**A coupon code didn't apply.**
See [Coupons & Redeem Codes](../subscriptions/coupons.md) for the common reasons; the preview shows the exact failure.

## Permissions

**Who can manage events?**
Discord Manage Server holders always; otherwise the event's mod role: `scrims-mod`, `tourney-mod`, `single-match-mod`, `daily-scrims-mod` (created by `/setup`).

**Why is a button disabled?**
It encodes state — wrong window state, locked round, missing required field, or a permission/plan gate. See [Dashboard Troubleshooting](../dashboard/troubleshooting-dashboard.md).

**The bot won't grant the success role.**
The role is above the bot's highest role. Move the bot's role up in the role list.

## Getting help

- Run `/support` for the support server invite.
- Report bugs with `/bugreport`; request features with `/featurerequest`.
- Policy documents: `/policy`.
