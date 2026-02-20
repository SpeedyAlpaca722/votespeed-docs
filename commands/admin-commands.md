# Admin Commands

All admin commands use the `/vote admin` prefix and require the `votespeed.admin` permission.

## Command Overview

| Command | Description |
|---|---|
| `/vote admin help` | Shows admin help menu |
| `/vote admin reload` | Reload all configuration files |
| `/vote admin debug` | Toggle debug mode |
| `/vote admin simulate <player> <service>` | Simulate a test vote |
| `/vote admin setpoints <player> <amount>` | Set a player's vote points |
| `/vote admin addpoints <player> <amount>` | Add vote points to a player |
| `/vote admin removepoints <player> <amount>` | Remove vote points from a player |
| `/vote admin setvotes <player> <amount>` | Set a player's total vote count |
| `/vote admin setstreak <player> <amount>` | Set a player's vote streak |
| `/vote admin reset <player>` | Reset all data for a player |
| `/vote admin resetall` | Reset ALL player data |
| `/vote admin info <player>` | View detailed player information |

## Detailed Usage

### /vote admin reload

Reloads all configuration files without restarting the server:

- `config.yml`
- `sites.yml`
- `shop.yml`
- `gui.yml`
- `rewards.yml`
- Language files

> **Note:** Changes to `receiver.port` or `storage.type` may require a full server restart.

### /vote admin debug

Toggles debug mode on/off. When enabled, detailed information is logged to the console, including:

- Incoming vote data (player name, service, timestamp)
- Reward processing details
- Hook registration and detection

### /vote admin simulate \<player> \<service>

Simulates a vote as if it came from a real vote site. Useful for testing:

```
/vote admin simulate Steve TopG
```

This triggers all rewards, effects, and point awards as a real vote would.

### /vote admin info \<player>

Shows comprehensive player data:

```
--- Admin Info: Steve ---
UUID: 12345678-1234-1234-1234-123456789abc
Total votes: 42
Today: 3 | Week: 12 | Month: 42
Streak: 7 | Best: 14
Points: 42
Last vote: 2024-01-15 14:30
Votes per site:
  - TopG: 20
  - PlanetMinecraft: 22
```

### /vote admin resetall

**Caution:** This permanently deletes ALL player data. Use with extreme care. There is no undo.

## Console Usage

All admin commands can be run from the server console. When running from console, the player name is always required:

```
vote admin simulate Steve TopG
vote admin info Steve
```
