# Rewards (rewards.yml)

The reward system defines what players receive when they vote. VoteSpeed supports multiple reward types with conditions, chances, and special command prefixes.

**Location:** `plugins/VoteSpeed/rewards.yml`

## Basic Structure

```yaml
rewards:
  reward-name:
    commands:
      - "give %player% diamond 1"
    player-message: "&aYou received a diamond!"
    broadcast-message: ""
    chance: 100
```

| Option | Description | Required |
|---|---|---|
| `commands` | List of commands to execute. Run as console. | Yes |
| `player-message` | Message sent to the voting player. Empty = no message. | No |
| `broadcast-message` | Message broadcast to all players. Empty = no broadcast. | No |
| `chance` | Probability (1-100) that this reward triggers. | Yes |

## Command Placeholders

These placeholders work in all reward commands and messages:

| Placeholder | Description |
|---|---|
| `%player%` | Player's name |
| `%uuid%` | Player's UUID |
| `%service%` | Vote site name |
| `%streak%` | Current streak |
| `%bestStreak%` | Best streak ever |
| `%totalVotes%` | Total vote count |
| `%dayVotes%` | Votes today |
| `%weekVotes%` | Votes this week |
| `%monthVotes%` | Votes this month |
| `%points%` | Current point balance |

## Reward Types

### Default Reward (Always)

Triggers on every vote (with the specified chance):

```yaml
  default:
    commands:
      - "give %player% diamond 1"
      - "[money] 100"
    player-message: "&aYou received &e1 Diamond &a+ &e100$&a!"
    chance: 100
```

### Per-Service Reward

Only triggers when the vote comes from a specific site:

```yaml
  topg-bonus:
    condition:
      service: "TopG"
    commands:
      - "give %player% emerald 3"
    player-message: "&aTopG Bonus: &e3 Emeralds!"
    chance: 100
```

### Streak Reward

Triggers when the player has maintained a minimum daily streak:

```yaml
  streak-bonus:
    condition:
      min-streak: 7
    commands:
      - "give %player% netherite_ingot 1"
    player-message: "&6Streak Bonus! &e1 Netherite Ingot &7(Streak: %streak%)"
    chance: 100
```

### Milestone Reward

Triggers every N total votes (e.g., every 50 votes):

```yaml
  milestone-50:
    condition:
      total-votes-multiple: 50
    commands:
      - "give %player% elytra 1"
    player-message: "&6&lMILESTONE! &aYou reached &e%totalVotes% Votes&a!"
    broadcast-message: "&6%player% &7reached &e%totalVotes% &7Votes!"
    chance: 100
```

### Random Pool

Selects one random reward from a weighted pool:

```yaml
  random-pool:
    type: random-pool
    pool:
      - commands: ["give %player% golden_apple 5"]
        weight: 50
      - commands: ["give %player% diamond 10"]
        weight: 30
      - commands: ["give %player% netherite_scrap 2"]
        weight: 20
    player-message: "&eYou received a random reward!"
    chance: 100
```

Weights are relative. In the example above:
- Golden apples: 50% chance (50 / 100)
- Diamonds: 30% chance (30 / 100)
- Netherite scraps: 20% chance (20 / 100)

## Special Command Prefixes

Instead of running regular server commands, you can use these prefixes for direct integrations:

| Prefix | Description | Example |
|---|---|---|
| `[money] <amount>` | Vault/VaultUnlocked economy deposit | `[money] 100` |
| `[luckperms] group <group> <duration>` | Temporary LuckPerms group | `[luckperms] group vip 24h` |
| `[luckperms] permission <node> <duration>` | Temporary LuckPerms permission | `[luckperms] permission fly.use 7d` |
| `[tokens] <amount>` | TokenManager tokens | `[tokens] 50` |
| `[crate] <crate> <amount>` | CrazyCrates key | `[crate] vote 1` |
| `[phoenixcrate] <crate-id> <amount>` | PhoenixCrates key | `[phoenixcrate] votecrate 1` |

### Duration Formats (LuckPerms)

| Format | Duration |
|---|---|
| `30m` | 30 minutes |
| `24h` | 24 hours |
| `7d` | 7 days |
| `1w` | 1 week |

### Example: Streak VIP Rank

```yaml
  streak-vip:
    condition:
      min-streak: 7
    commands:
      - "[luckperms] group vip 24h"
    player-message: "&6Streak Bonus! &eVIP rank for 24 hours!"
    chance: 100
```

## VoteParty Rewards

VoteParty rewards are separate and given to **all online players** when the party triggers:

```yaml
voteparty-rewards:
  commands:
    - "give %player% golden_apple 5"
    - "eco give %player% 500"
  player-message: "&d&lVOTEPARTY! &aYou received party rewards!"
```

See [VoteParty](../features/voteparty.md) for more details.

## External Reward Files

```yaml
external-reward-files: true
```

When enabled, VoteSpeed also loads reward files from `plugins/VoteSpeed/rewards/`. This lets you organize rewards into separate files. See [External Reward Files](../advanced/external-rewards.md).

## Reward Processing Order

1. All rewards in `rewards.yml` are checked in order (top to bottom)
2. For each reward, conditions are checked first
3. If conditions pass, the chance roll is made
4. If the chance succeeds, commands are executed
5. Multiple rewards can trigger from a single vote
