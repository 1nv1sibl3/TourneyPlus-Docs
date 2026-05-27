# Pricing & Checkout

Routes:
- `/pricing`
- `/payment?planId=...`

## Pricing Page Behavior

- Plan cards adjust by plan configuration.
- Custom category plans should show as **CUSTOM** where applicable.
- Layout should auto-wrap cleanly for uneven card counts.

[IMG: Pricing cards and CTA layout]

## Trial Messaging

Landing pages may show trial promo strips.
Recommended messaging includes:
- 2-week trial
- no card required
- direct link to pricing page

## Payment Page

For server-scoped plans:
- server selector should be visible
- purchase binds to selected server

For user-scoped plans:
- no server selector required

## Invoice and Email

On successful purchase or assignment flows, invoice-related notifications can be sent through email manager/resend integration.

## Time Units

Current month unit policy target: 28 days (where configured by product rules).

[VIDEO: Plan selection to successful checkout]