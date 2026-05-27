# Support Escalation Playbook

## Priority Levels

- **P0**: system-wide outage, mass action failures
- **P1**: event lifecycle blocked for active customers
- **P2**: degraded behavior with workaround
- **P3**: cosmetic/UI issues

## First Response Template

1. Acknowledge issue scope.
2. Ask for event id / server id / timestamp.
3. Confirm whether bot, dashboard, or both are impacted.
4. Provide temporary workaround if available.

## Diagnostic Data to Collect

- server id
- event type + event id
- screenshot/message ids if applicable
- exact error text or screenshot
- action sequence user performed

## Escalation Paths

- queue/inference issues -> worker/job team
- discord command/action mismatch -> bot integration team
- subscription/billing/email -> admin/backend team
- frontend rendering/UX -> dashboard team

## Closure Checklist

- root cause identified
- fix deployed
- user confirmed resolved
- documentation updated if behavior changed

[IMG: Escalation flow diagram]