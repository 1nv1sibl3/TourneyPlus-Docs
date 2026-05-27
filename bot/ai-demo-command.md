# AI Demo Command

Command: `aidemo`

Purpose: queue a screenshot for AI demo processing in a restricted channel, without affecting live event scoring.

## Usage Pattern

`!aidemo <ign1> <ign2> <ign3> <ign4>` + attach screenshot in same message.

## Constraints

- command is channel-restricted
- intended for showcase/testing
- should not mutate live event score tables

## Result Embed Expectations

Demo result message should include:
- job id
- submitted by
- extracted rank
- extracted kills
- position point
- total points

## Notes

This is an exception path and should remain isolated from core event lifecycle.

[IMG: aidemo command + result embed]