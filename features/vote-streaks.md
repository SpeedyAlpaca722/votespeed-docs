# Vote Streaks

Vote streaks track how many consecutive days a player has voted. Streaks are a powerful motivator to encourage daily voting.

## How Streaks Work

1. A player votes on Day 1 → Streak = 1
2. They vote again on Day 2 → Streak = 2
3. They vote again on Day 3 → Streak = 3
4. They **miss** Day 4 → Streak resets to 0
5. They vote on Day 5 → Streak = 1

Streaks reset at the configured daily reset time (default: midnight in your timezone).

## Configuration

```yaml
# config.yml
timezone: "Europe/Berlin"

reset:
  daily-reset-time: "00:00"
  check-interval-minutes: 5
```

| Option | Description |
|---|---|
| `timezone` | Timezone for determining when a "day" starts/ends |
| `daily-reset-time` | Time of day when the daily period resets |
| `check-interval-minutes` | How often the plugin checks for needed resets |

## Viewing Streaks

Players can see their streak with:

```
/vote stats
```

Output: `Your stats: 42 total | Streak: 7 | Best: 14 | Points: 42`

## Streak-Based Rewards

You can create rewards that only trigger at certain streak levels:

```yaml
# rewards.yml
rewards:
  streak-bonus:
    condition:
      min-streak: 7
    commands:
      - "give %player% netherite_ingot 1"
    player-message: "&6Streak Bonus! &e1 Netherite Ingot &7(Streak: %streak%)"
    chance: 100
```

This reward triggers on every vote where the player's streak is 7 or higher.

### Streak Bonus Points

Award extra points based on streak length:

```yaml
# config.yml
points:
  enabled: true
  per-vote: 1
  per-streak-bonus: 1    # +1 bonus point per streak day
```

### Streak VIP Rank

Give a temporary LuckPerms rank for maintaining a streak:

```yaml
# rewards.yml
  streak-vip:
    condition:
      min-streak: 7
    commands:
      - "[luckperms] group vip 24h"
    player-message: "&6Streak Bonus! &eVIP rank for 24 hours!"
    chance: 100
```

## Admin Streak Management

| Command | Description |
|---|---|
| `/vote admin setstreak <player> <amount>` | Set a player's streak |
| `/vote admin info <player>` | View detailed player info including streak |

## Placeholders

| Placeholder | Description |
|---|---|
| `%streak%` | Current streak |
| `%bestStreak%` | Best streak ever achieved |
