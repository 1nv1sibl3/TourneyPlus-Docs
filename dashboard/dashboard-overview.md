# Dashboard Overview

Main sidebar sections:
- Dashboard
- Tournaments
- Scrims
- Matches
- Results Hub
- Prize Pool
- Upgrade Plan
- Profile
- Invite Bot

[IMG: Dashboard sidebar full view]

## Design Goal

The dashboard is your visual control panel for event lifecycle:
1. Create event
2. Register teams
3. Schedule matches
4. Open screenshot windows
5. Review and finalize results
6. Publish leaderboard

## Important Navigation Notes

- **Tournaments** and **Scrims** have separate management flows.
- **Matches** provides match-level visibility.
- **Results Hub** is where manual corrections happen.
- **Profile** includes server subscription details and usage activity.

## Operational Rules to Remember

- If a button appears locked/disabled, usually a permission, subscription, or lifecycle state is blocking the action.
- For real-time state changes, wait for websocket sync before repeated clicking.
- If state looks stale, use refresh action where available.

[VIDEO: Event lifecycle from create to publish]