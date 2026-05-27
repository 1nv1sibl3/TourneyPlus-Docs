# Bot Troubleshooting

## Registration Started But Not Capturing Entries

Checks:
1. registration channel id mapping still valid
2. event record still exists
3. runtime state restored after restart
4. bot has message read/send permissions

## Persistent Views Not Restored

At startup, verify log line for persistent views/runtime restoration count.
If zero unexpectedly, check state cache/persistence records.

## Slash Commands Missing or Duplicated

- sync logic can lag per guild/global scope
- avoid multiple overlapping sync triggers
- confirm command registration strategy per cog

## Screenshot Publish Missing Data

If rank/kill/pos appear as zero unexpectedly:
- inspect processing output
- verify dashboard corrections were applied
- check publish payload mapping

## Integration WS Errors

Common causes:
- missing/deleted channel
- stale event id referenced by dashboard command
- command topic fired for deleted event

## Queue Output Too Large

Use pagination in queue commands for large servers to avoid Discord message limits.

[IMG: Common bot-side error checklist]