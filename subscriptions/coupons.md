# Coupons & Redeem Codes

Coupon codes applied at checkout for a discount, bonus (top-up) entitlements, or both.

## Applying a coupon

1. Start checkout at `/payment?planId=…`.
2. Enter the code in the **coupon** field and apply.
3. The checkout preview updates: base amount, discount, and final amount. If the coupon carries top-up entitlements, they are listed too.
4. Complete the payment — the coupon is locked to the transaction and the entitlements merge into your assignment.

Codes are case-insensitive (normalized to upper case). A coupon preview that fails shows the reason (invalid, expired, minimum order not met, not allowed for this plan/scope).

## What a coupon can do

| Effect | Example |
| --- | --- |
| **Percent discount** | 20% off, optionally capped at a maximum discount |
| **Flat discount** | A fixed amount off, subject to a minimum order |
| **Top-up entitlements** | Bonus quota/features granted with the resulting assignment |

Coupons can be restricted by:

- **Allowed plans** — only certain plans.
- **Allowed users / servers** — only certain buyers.
- **Redemption limits** — total and per-user caps.
- **Validity window** — start/end dates.
- **Status/visibility** — active/inactive; private coupons are not advertised but still redeemable at checkout.

## Coupon-backed bonus entitlements

Top-up entitlements from a coupon are merged into the assignment's metadata and shown on your profile page (with a count of coupon-provided entitlements). They last as long as the assignment they were purchased with.

## Trials vs coupons

Trials are separate: a trial plan assignment granted on its own rules (see [Pricing & Checkout](../dashboard/pricing-checkout.md)). Coupons modify a purchase you're making.

## Troubleshooting

| Symptom | Cause |
| --- | --- |
| *Invalid coupon* | Code doesn't exist, is inactive, or its window has passed |
| *Minimum order not met* | The order total is below the coupon's minimum |
| *Not allowed for this plan* | The coupon is restricted to other plans |
| *Redemption limit reached* | The coupon's total or per-user cap is exhausted |
| Discount missing after payment | The code snapshot is stored on the redemption record — check the invoice; contact support with the transaction id if it differs from the preview |

## Where codes come from

Codes are distributed by the TourneyPlus team (promotions, partnerships, compensations). There is no public code listing; if you received a code, apply it at checkout as above.
