# Job Manager

Route: `/admin/jobs`

## Purpose

Operational visibility for screenshot processing queue.

## Default View Recommendation

Show `queued` by default so operators focus on pending work first.
Use filters for succeeded/failed/history when needed.

## Key Columns

- job id
- event id
- match/team references
- status
- attempts
- updated time

## Troubleshooting Patterns

- repeated failures: check source screenshot availability
- stale processing: check worker heartbeat
- event mismatch: verify event still exists and binding did not change

[IMG: Job manager with status filters]