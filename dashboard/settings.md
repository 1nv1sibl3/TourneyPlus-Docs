# Settings & Bot Customization

Route: `/settings`. Per-server settings that control how the bot looks and behaves in the selected server, plus the Discord-side `/customize` command group for bot branding.

## Bot customization (`/customize`)

Per-server bot profile: nickname, avatar, and banner shown **only in that server**. Requires **Administrator**, plus a subscription entitlement for bot customization (`guild.bot.customize`) — it's a premium feature.

```
/customize                    → opens the customization panel
/customize nick <nickname>    → set or clear (blank) the nickname
/customize avatar [url]       → set (or clear) the per-server avatar
/customize banner [url]       → set (or clear) the per-server banner
```

Details:

- Nickname: max 32 characters.
- Images: upload an attachment or give a direct URL; minimum 128×128 px; auto-compressed under 10 MB (animated GIFs can't be compressed — oversized GIFs are rejected).
- Settings persist in the database and are re-applied on sync — but if the subscription lapses, branding reverts to global defaults (and restores when the subscription returns).
- The same controls exist on the dashboard settings page.

<!-- screenshot: dashboard-settings-bot-profile -->

## Dashboard settings pages

The `/settings` section groups per-server configuration:

| Area | What it controls |
| --- | --- |
| **Bot profile** | The per-server nickname/avatar/banner above |
| **Modlog** | Server moderation logging configuration |
| **Autorole** | Automatic role assignment on member join |
| **Tags** | Custom tag commands |
| **Sticky messages** | Persistent messages re-pinned after channel activity |
| **Embeds** | Embed templates sendable to channels (with placeholder support) |

Each area mirrors a bot feature; editing here applies in Discord within seconds.

## Embed placeholders

Embeds (from the dashboard or `/embed`) support live placeholders resolved at send time:

| Placeholder | Replaced with |
| --- | --- |
| `{user}`, `{user.mention}` | The acting user's mention |
| `{user.name}`, `{user.id}`, `{user.avatar}` | Name, id, avatar URL |
| `{server}`, `{server.id}`, `{guild}` | Server name and id |
| `{member_count}` | Server member count |
| `{channel}`, `{channel.name}` | Target channel mention and name |

## Server settings and moderation status

Servers can be **active**, **suspended** (read-only), or **banned** (no access) platform-side. If a selected server shows a suspended/banned tag in the server selector, contact support — the dashboard shows the reason where available.
