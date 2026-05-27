# Analytics

Route: `/admin/analytics`

## Expected Coverage

- user/server growth overview
- live match operations snapshot
- screenshot queue metrics
- event hosting distribution

## Event Distribution Tab

Include pie chart for:
- total hosted events
- scrim/tier count
- tournament count
- single match count

Recommendation:
- include deleted historical events when computing hosted totals if product policy tracks all hosted events.

## Export

Export actions should produce valid output (PDF) and not open blank tabs.

## Dynamic vs Static Indicators

If % trend cards are static placeholders, either:
- make them truly dynamic, or
- remove them to avoid misleading operators.

## Activity Feed

Use scrollable feed for long history.
Remove irrelevant icons/noise.

[IMG: Analytics pie chart + export control]