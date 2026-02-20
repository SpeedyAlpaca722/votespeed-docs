# Discord Webhook

VoteSpeed can log votes to a Discord channel using webhooks.

## Configuration

```yaml
# config.yml
discord:
  enabled: false
  webhook-url: "https://discord.com/api/webhooks/YOUR_WEBHOOK_URL"
  embed-color: "#FFD700"
  message: "%player% voted on %service%! (Total: %totalVotes%)"
```

| Option | Description | Default |
|---|---|---|
| `enabled` | Enable Discord webhook integration | `false` |
| `webhook-url` | Your Discord webhook URL | — |
| `embed-color` | Hex color code for the embed sidebar | `#FFD700` (gold) |
| `message` | Message content sent to Discord | — |

## Setup

### 1. Create a Discord Webhook

1. Open your Discord server settings
2. Go to **Integrations** → **Webhooks**
3. Click **New Webhook**
4. Choose a name (e.g., "VoteSpeed") and the target channel
5. Click **Copy Webhook URL**

### 2. Configure VoteSpeed

```yaml
discord:
  enabled: true
  webhook-url: "https://discord.com/api/webhooks/1234567890/abcdefg..."
  embed-color: "#FFD700"
  message: "%player% voted on %service%! (Total: %totalVotes%)"
```

### 3. Reload

```
/vote admin reload
```

## Message Placeholders

| Placeholder | Description |
|---|---|
| `%player%` | Player name |
| `%service%` | Vote site name |
| `%totalVotes%` | Player's total votes |
| `%streak%` | Current streak |
| `%points%` | Current points |

## DiscordSRV Integration

For more advanced Discord integration (linked accounts, role sync, etc.), see the [DiscordSRV Integration](../integrations/discordsrv.md) page.
