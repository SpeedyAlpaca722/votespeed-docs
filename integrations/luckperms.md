# LuckPerms

VoteSpeed integrates with [LuckPerms](https://luckperms.net/) to grant temporary ranks and permissions as vote rewards.

## Configuration

```yaml
# config.yml
hooks:
  luckperms:
    enabled: true
```

## Temporary Group (Rank)

Grant a temporary group/rank when a player votes:

```yaml
# rewards.yml
rewards:
  streak-vip:
    condition:
      min-streak: 7
    commands:
      - "[luckperms] group vip 24h"
    player-message: "&6Streak Bonus! &eVIP rank for 24 hours!"
    chance: 100
```

**Syntax:** `[luckperms] group <group-name> <duration>`

## Temporary Permission

Grant a temporary permission node:

```yaml
rewards:
  fly-reward:
    commands:
      - "[luckperms] permission essentials.fly 12h"
    player-message: "&aYou can fly for 12 hours!"
    chance: 100
```

**Syntax:** `[luckperms] permission <permission-node> <duration>`

## Duration Formats

| Format | Duration |
|---|---|
| `30m` | 30 minutes |
| `1h` | 1 hour |
| `24h` | 24 hours |
| `7d` | 7 days |
| `1w` | 1 week |

## Use Cases

### Daily VIP for Streaks

```yaml
  daily-vip:
    condition:
      min-streak: 3
    commands:
      - "[luckperms] group vip 24h"
    player-message: "&6+24h VIP for your 3-day streak!"
    chance: 100
```

### Weekly Donor Rank for Milestones

```yaml
  donor-milestone:
    condition:
      total-votes-multiple: 100
    commands:
      - "[luckperms] group donor 7d"
    player-message: "&d&l100 Votes! &eDonor rank for 1 week!"
    chance: 100
```

### Temporary Fly Permission

```yaml
  fly-vote:
    commands:
      - "[luckperms] permission essentials.fly 1h"
    player-message: "&bFly for 1 hour!"
    chance: 25
```

## Notes

- The LuckPerms plugin must be installed and loaded before VoteSpeed
- Temporary permissions/groups stack — if a player already has the group, the duration is extended
- VoteSpeed uses the LuckPerms API directly, not commands — this is faster and more reliable
