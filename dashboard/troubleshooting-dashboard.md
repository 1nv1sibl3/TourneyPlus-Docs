# Dashboard Troubleshooting

## Event Not Refreshing After Action

Checks:
1. Wait for websocket confirmation/state update.
2. Manual refresh page.
3. Verify bot integration websocket is connected.

## Registration Open/Close Button Misbehavior

- Avoid double clicks/spam.
- Confirm action success before next action.
- Check if event is suspended/banned (admin policies).

## Screenshot Window Open Fails

Common causes:
- target channel missing/deleted
- permission mismatch
- duplicated schedule records with wrong match mapping

## Leaderboard Looks Wrong

- Confirm points formula is applied (position + kills).
- Check conflict highlights.
- Reopen results hub and verify raw extracted values.

## Queue/Processing Looks Stuck

- Review Job Manager status filters.
- Check worker heartbeat/retry state.
- verify job not permanently failed due source screenshot issue.

## Profile Usage Activity Empty

- confirm server context selection
- check whether events are usage-logged source vs derived snapshot only
- validate filter mode (My Usage / All Users)

## Deletion Side Effects

If shared channels were reused across events, deletion behavior should preserve registration/slotlist channels as per latest policy.

[IMG: Common error checklist card]