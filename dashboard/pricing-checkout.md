# Pricing & Checkout

Routes: `/pricing` (plan listing), `/payment` (checkout with `?planId=…` or `?planCode=…`), and `/billing` (your billing hub).

## The Billing page

`/billing` is the hub for everything you've bought:

| Section | What it shows |
| --- | --- |
| **Subscribed servers** | The servers covered by your plans, with their active plan per server |
| **Redeem a coupon** | Enter a code you received — some codes grant a plan directly, others add bonus entitlements. Applies to your account, or to the server picked in the usage section |
| **Quota usage** | Per-server quota consumption (pick the server to inspect) |
| **Upgrade your plan** | The plan catalog with one-click checkout |
| **Transactions** | Your full invoice history — date, plan, period, invoice number, scope, amount, and status (Paid / Pending / Failed / Refunded) |

The same billing summary (the selected server's plan and recent transactions) is available from the top bar without leaving what you're doing.

## The pricing page

Public, self-serve-purchasable plans are listed with name, description, price, and duration. Plans can also be admin-managed (not listed). Custom-category plans may appear labeled **CUSTOM**. A trial banner on the marketing pages links here when a trial is available.

## Checking out

1. Open `/payment?planId=…` (every plan card links here).
2. Sign in with Discord if you haven't.
3. Choose the **scope**:
   - **Server-scoped plans** require selecting a server — you must have **Manage Server** on it.
   - **User-scoped plans** apply to your account across servers; no server selection needed.
   - **User + server** scoped plans bind your account to one server.
4. Optionally apply a **coupon code** — the checkout preview updates with the discount (and any bonus entitlements the coupon carries). See [Coupons & Redeem Codes](../subscriptions/coupons.md).
5. Pay via the Razorpay checkout (card/UPI/netbanking, in INR).

<!-- screenshot: dashboard-payment-checkout -->

## After payment

- The plan assignment activates when the payment is captured (server-to-server webhook; not dependent on your browser staying open).
- The assignment queues **after** any currently active assignment on the same scope — you never lose paid time by buying early.
- An invoice is emailed to you, and expiry reminders are scheduled.
- Your active plan shows on `/profile` (dashboard) and via `/premium` (Discord).

## Trials

Trial plans may be limited to **once per user** or **once per server** — attempting a second one returns *"Trial already consumed for this user/server."* Trial assignments behave like active ones (entitlements and quotas apply) and show a **Trial** status.

## Scope and permission rules at checkout

- Self-serve purchases can only target **your own** user scope.
- Global-scope subscriptions cannot be self-purchased.
- You need Manage Server on any server you're buying for.
- The plan's configuration itself decides which scopes it allows (`user`, `server`, `user_server`).

## Duration note

A "monthly" subscription period is **28 days**, matching the quota window model. Plan durations and prices are defined per plan; currency defaults to INR.

## Errors

| Message | Meaning |
| --- | --- |
| *Trial already consumed for this user / server.* | The trial's once-per limit was already used. |
| *You do not have permission to purchase this plan for the selected server.* | You lack Manage Server on the chosen server. |
| *Plan does not allow … scoped subscriptions.* | The selected scope isn't offered for that plan. |
| *Payment verification failed.* | The signature check failed — retry the checkout; if it persists, contact support with the transaction id. |

## Managing an existing subscription

From `/billing` you can view your servers, redeem codes, and browse transactions; from `/profile` you can view assignments, windows, and usage. Cancellation and refund handling follow the published [policies](https://tourneyplus.xyz/refund).
