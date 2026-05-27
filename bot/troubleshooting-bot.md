# Bot Troubleshooting

## Registration Opened But Entries Not Captured

Check:
1. correct registration channel is configured
2. event still exists and is active
3. bot can read/send messages in that channel

## Slash Command Not Visible

- allow a few minutes for sync
- check if command is disabled in your guild scope

## Leaderboard Values Look Wrong

- verify rank/kills in review screen
- confirm points formula (`position + kills`)
- republish only after corrections

## Screenshot Action Failed

Check:
- correct match/group selected
- target channel still exists
- bot permissions are valid

## Large Queue Output

Use command filters or event id scope to reduce output size.