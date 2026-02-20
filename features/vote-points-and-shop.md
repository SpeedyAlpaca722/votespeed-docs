# Vote Points & Shop

The vote points system rewards players with points for each vote. Players can then spend these points in the Vote Shop.

## How Points Work

Every time a player votes, they receive points based on your configuration:

```yaml
# config.yml
points:
  enabled: true
  per-vote: 1
  per-streak-bonus: 0
```

| Option | Description |
|---|---|
| `per-vote` | Base points awarded per vote |
| `per-streak-bonus` | Extra points per streak day (e.g., `1` = streak of 5 gives 5 bonus points) |

**Example:** With `per-vote: 1` and `per-streak-bonus: 1`, a player with a 7-day streak earns 8 points per vote (1 base + 7 bonus).

## Checking Points

Players can check their balance with:

```
/vote points
```

Output: `Your vote points: 42`

## The Vote Shop

The shop is a GUI where players spend their points. Open it with:

```
/vote shop
```

### Configuring Shop Items

See [Shop Configuration](../configuration/shop.md) for the full shop.yml reference.

### Quick Example

```yaml
# shop.yml
shop-items:
  diamond-pack:
    slot: 10
    material: DIAMOND
    name: "&bDiamond Pack"
    lore:
      - "&75x Diamonds"
      - "&7Price: &6%price% Points"
    price: 5
    commands:
      - "give %player% diamond 5"
```

## Admin Point Management

Admins can manage player points with these commands:

| Command | Description |
|---|---|
| `/vote admin setpoints <player> <amount>` | Set a player's points |
| `/vote admin addpoints <player> <amount>` | Add points to a player |
| `/vote admin removepoints <player> <amount>` | Remove points from a player |

All commands require `votespeed.admin` permission.

## Disabling the Point System

To completely disable vote points, set in `config.yml`:

```yaml
points:
  enabled: false
```

To disable only the shop while keeping points, set in `shop.yml`:

```yaml
enabled: false
```
