# Vote Reminders

VoteSpeed can remind players to vote, both when they log in and periodically while playing.

## Configuration

```yaml
# config.yml
reminder:
  enabled: true
  login-reminder: true
  periodic:
    enabled: false
    interval-minutes: 60
```

| Option | Description | Default |
|---|---|---|
| `enabled` | Master switch for all reminders | `true` |
| `login-reminder` | Remind players on join if they have available vote sites | `true` |
| `periodic.enabled` | Send periodic reminders to online players | `false` |
| `periodic.interval-minutes` | Interval between periodic reminders (minutes) | `60` |

## Login Reminder

When a player joins the server, VoteSpeed checks if they have any vote sites available (not on cooldown). If so, a message is sent:

```
You can vote again on 3 sites! /vote gui
```

This only triggers if the player has at least one available site.

## Periodic Reminder

When enabled, a reminder is broadcast to all online players at the configured interval:

```
Don't forget to vote! /vote gui
```

## Customizing Messages

In your language file:

```yaml
vote-reminder-login: "&eYou can vote again on &6%count% &esites! &7/vote gui"
vote-reminder-periodic: "&eDon't forget to vote! &7/vote gui"
```

| Placeholder | Description |
|---|---|
| `%count%` | Number of available vote sites |
