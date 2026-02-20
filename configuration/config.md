# Main Config (config.yml)

The main configuration file controls all core settings of VoteSpeed.

**Location:** `plugins/VoteSpeed/config.yml`

## Language

```yaml
language: en
```

Sets the plugin language. VoteSpeed ships with `en` (English) and `de` (German). See [Language Files](language.md) for customization.

## Votifier Receiver

```yaml
receiver:
  host: "0.0.0.0"
  port: 8192
  auto-port-finder: true
  disable-v1-protocol: false
  debug: false
  tokens:
    default: "CHANGE_ME"
```

| Option | Description | Default |
|---|---|---|
| `host` | IP address to bind the receiver to. `0.0.0.0` listens on all interfaces. | `0.0.0.0` |
| `port` | Port the Votifier receiver listens on. Must match your vote site config. | `8192` |
| `auto-port-finder` | If the port is busy, automatically find a free port. | `true` |
| `disable-v1-protocol` | Disable legacy Votifier v1 protocol (less secure). | `false` |
| `debug` | Log detailed receiver debug info to console. | `false` |
| `tokens.default` | NuVotifier v2 authentication token. **Change this!** Copy this token to your vote sites. | `CHANGE_ME` |

> **Tip:** You do NOT need a separate Votifier/NuVotifier plugin. VoteSpeed has a built-in receiver.

## Database

```yaml
storage:
  type: sqlite
  sqlite:
    file: "votes.db"
  mysql:
    host: "localhost"
    port: 3306
    database: "votespeed"
    username: "root"
    password: ""
```

| Option | Description | Default |
|---|---|---|
| `type` | Database type: `sqlite` or `mysql` | `sqlite` |
| `sqlite.file` | SQLite database filename (relative to plugin folder) | `votes.db` |
| `mysql.*` | MySQL connection settings (only used when `type: mysql`) | — |

See [Database](../advanced/database.md) for MySQL setup details.

## Anti-Duplicate Protection

```yaml
anti-duplicate:
  enabled: true
  ignore-seconds: 300
```

Prevents the same vote from being processed twice within the time window. This protects against vote sites sending duplicate votes.

| Option | Description | Default |
|---|---|---|
| `enabled` | Enable duplicate vote filtering | `true` |
| `ignore-seconds` | Time window (seconds) to consider votes as duplicates | `300` (5 min) |

## Timezone & Resets

```yaml
timezone: "Europe/Berlin"

reset:
  daily-reset-time: "00:00"
  check-interval-minutes: 5
```

| Option | Description | Default |
|---|---|---|
| `timezone` | Timezone for streak calculations and daily resets. Uses Java timezone IDs. | `Europe/Berlin` |
| `daily-reset-time` | Time of day when daily/weekly/monthly vote counters reset (HH:mm). | `00:00` |
| `check-interval-minutes` | How often the plugin checks if a reset is due. | `5` |

## Cache

```yaml
cache:
  enabled: true
  expiry-seconds: 60
```

Player data caching for improved performance. Reduces database queries.

## Update Checker

```yaml
update-checker:
  enabled: true
  resource-id: 0
```

Checks for new versions on startup and notifies admins on join.

## Online Requirement

```yaml
require-online: false
```

| Value | Behavior |
|---|---|
| `false` | Offline votes are stored in a queue and delivered when the player joins |
| `true` | Votes are only rewarded when the player is online at the time of voting |

## Vote Points

```yaml
points:
  enabled: true
  per-vote: 1
  per-streak-bonus: 0
```

| Option | Description | Default |
|---|---|---|
| `enabled` | Enable the vote points system | `true` |
| `per-vote` | Points awarded per vote | `1` |
| `per-streak-bonus` | Additional points per streak day (0 = disabled) | `0` |

## VoteParty

```yaml
voteparty:
  enabled: true
  votes-needed: 50
  reset-after-party: true
```

See [VoteParty](../features/voteparty.md) for full details.

## Vote Effects

```yaml
effects:
  broadcast:
    enabled: true
  actionbar:
    enabled: true
    message: "&a+1 Vote! Streak: %streak%"
  title:
    enabled: true
    title: "&6Thank you!"
    subtitle: "&eYou voted on %service%!"
    fade-in: 10
    stay: 40
    fade-out: 10
  sound:
    enabled: true
    name: "ENTITY_PLAYER_LEVELUP"
    volume: 1.0
    pitch: 1.0
```

See [Vote Effects](../features/vote-effects.md) for details.

## Vote Reminders

```yaml
reminder:
  enabled: true
  login-reminder: true
  periodic:
    enabled: false
    interval-minutes: 60
```

See [Vote Reminders](../features/vote-reminders.md) for details.

## Discord Webhook

```yaml
discord:
  enabled: false
  webhook-url: "https://discord.com/api/webhooks/YOUR_WEBHOOK_URL"
  embed-color: "#FFD700"
  message: "%player% voted on %service%! (Total: %totalVotes%)"
```

See [Discord Webhook](../features/discord-webhook.md) for details.

## Plugin Hooks

```yaml
hooks:
  economy:
    enabled: true
    provider: auto    # auto, vault, vaultunlocked
  luckperms:
    enabled: true
  tokenmanager:
    enabled: true
  crazycrates:
    enabled: true
  phoenixcrates:
    enabled: true
  itemsadder:
    enabled: true
  oraxen:
    enabled: true
  nexo:
    enabled: true
  discordsrv:
    enabled: true
```

Each hook can be individually enabled or disabled. Disabled hooks are ignored even if the corresponding plugin is installed. See [Integrations](../integrations/economy.md) for details on each hook.

## Bedrock Forms

```yaml
bedrock-forms:
  enabled: true
  shop-confirm-dialog: true
```

| Option | Description | Default |
|---|---|---|
| `enabled` | Show native Bedrock Forms instead of chest GUIs for Bedrock players | `true` |
| `shop-confirm-dialog` | Show a confirmation dialog before purchasing shop items | `true` |

Requires [Floodgate](../advanced/bedrock-support.md) on the server. See [Bedrock Support](../advanced/bedrock-support.md).

## Vote Forwarding (Proxy)

```yaml
forwarding:
  method: none
  pluginMessaging:
    channel: "votespeed:votes"
```

| Option | Description | Default |
|---|---|---|
| `method` | Forwarding method: `none`, `pluginMessaging` | `none` |
| `pluginMessaging.channel` | Plugin message channel (must match proxy config) | `votespeed:votes` |

See [Proxy Setup](../advanced/proxy-setup.md) for network configuration.
