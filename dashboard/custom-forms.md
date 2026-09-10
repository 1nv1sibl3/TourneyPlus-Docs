# Custom Forms

Custom forms collect structured registration data — Name, Email, Phone, and teammate tags — and assign a role on completion. They are the dashboard-managed counterpart to the bot's `/customform` command, sharing the same configuration.

Manage them at `/custom-forms`. Requires Discord Manage Server on the selected server.

<!-- screenshot: dashboard-custom-forms -->

## What a form is

Each form configuration defines:

| Setting | Meaning |
| --- | --- |
| Target channel | Where the registration form message is posted |
| Role to assign | The role granted on successful completion |
| Game | Which game the team profile is stored under |
| Team size cap | Maximum players per team (4, 5, or 6) |
| Embed title / description | The public form message's text |
| Thumbnail / banner | Custom images (falls back to the server icon) |
| Team Profile collector | Also collect each player's IGN and UID into an editable team roster |
| Confirmation channel | Where teammates get tagged on submission |
| Role scope | Leader only, or all team members |

## Deploying a form

Saving posts (or edits in place) a persistent registration message in the target channel with a **Register** button. Players click it, fill the modal (name, email, phone, and select teammates), and on submission:

1. The configured role is granted (leader only or whole team, per Role Scope).
2. Teammates are tagged in the confirmation channel, if set.
3. A **Team Profile** roster is created or updated (when the collector is enabled).
4. The submission is appended to the immutable submission log.

The same message is kept in sync whether you save from Discord or the dashboard — both surfaces edit the identical configuration and message.

## Team Profiles

With the collector enabled, each leader owns an editable roster per server per game: team name and members with their IGN/UID. These rosters power **Team Profile registration** on events (the Register-button flow) and auto-fill future form submissions. Rosters live separately from the submission log, so editing a roster never rewrites past submissions.

## Submission data

Every submission is logged append-only with leader, team name, game, members, and collected answers. Even deleting the form preserves registrant data (the log references survive with nulls).

You can **download submissions as CSV** from the dashboard — the column widths survive form deletion because the data is denormalized onto each submission row.

## Editing and maintenance

- Editing a form edits its live message in place.
- **Resend** deletes and re-posts the message (fixes deleted messages or permission changes).
- Deleting a form removes the configuration and its live message, but the submission log is preserved.
- If the target channel is deleted or the bot loses access, saving still records the configuration but the message can't be delivered — fix the channel and use Resend.

## Moderation notes

- The `/customform` bot command opens the same configuration UI in Discord.
- Answer fields are length-limited in the modal (Full Name 150, Email 255, Phone 255 characters) matching the profile columns — oversized answers are rejected client-side.
