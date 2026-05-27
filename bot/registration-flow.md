# Registration Flow

## Open Registration

From manager UI, open registration for the selected event.
Bot posts registration embed in configured channel.

## User Registration

Users submit tags/format per event rule.
Validation typically checks:
- mention count
- duplicate rules
- member eligibility
- IGN/profile completeness rules

## Missing IGN Path

If member IGN is missing:
- member gets DM prompt to update profile
- registration remains pending/incomplete
- once all required profiles are complete, status auto-updates

## Slot List Updates

Slot list should reflect real-time occupied/available counts, including reopen cases.

## Close Registration

Closing registration stops new intake and finalizes current slot list.

## Important Edge Cases

- shared registration channels across events should be handled carefully
- deletion flow should not unintentionally destroy another active event
- registration state should survive restart (persistent runtime state)

[IMG: Registration embed + slot list example]