# Billing & Email

Routes:
- `/admin/billing`
- `/admin/email`

## Billing Viewer

Use to inspect:
- transactions
- plan purchase metadata
- assignment source differences (checkout vs admin assignment)

Recommended row clarity:
- payment status only when truly active/paid
- server link text should be readable and relevant
- activity period should be meaningful duration context

## Email Manager (Resend)

Current practical goal:
- send manual custom/template emails
- resend invoice email for selected invoice record
- keep dashboard-side load minimal and defer to Resend capabilities

## Contact Sync

Contact sync should run on first successful user login/signup event, not continuous DB polling.

## Rate Limit Awareness

Resend free tier rate limit can be low (example: 2 req/sec).
Throttle admin list/send calls to avoid 429 errors.

## Invoice Email Data

Invoice template variables should support:
- plan name/code
- server name
- amount/coupon/final amount
- invoice number
- source label (e.g. razorpay_checkout, admin_assignment)
- subscription start/end

[IMG: Admin email send panel]