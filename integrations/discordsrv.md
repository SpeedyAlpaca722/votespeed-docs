# DiscordSRV

VoteSpeed supports [DiscordSRV](https://www.spigotmc.org/resources/discordsrv.18494/) for extended Discord integration.

## Configuration

```yaml
# config.yml
hooks:
  discordsrv:
    enabled: true
```

## Features

When DiscordSRV is detected and enabled, VoteSpeed can leverage DiscordSRV's features for vote-related Discord interactions.

## Simple Discord Integration

For basic vote logging to Discord, you don't need DiscordSRV. VoteSpeed has a built-in [Discord Webhook](../features/discord-webhook.md) feature:

```yaml
# config.yml
discord:
  enabled: true
  webhook-url: "https://discord.com/api/webhooks/..."
  message: "%player% voted on %service%!"
```

## When to Use DiscordSRV vs Webhook

| Feature | Built-in Webhook | DiscordSRV |
|---|---|---|
| Vote logging | ✅ | ✅ |
| Account linking | ❌ | ✅ |
| Role sync | ❌ | ✅ |
| Two-way chat | ❌ | ✅ |
| Setup complexity | Simple | More complex |

Use the built-in webhook for simple vote logging. Use DiscordSRV if you need account linking, role sync, or other advanced features.
