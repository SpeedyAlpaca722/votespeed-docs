# TokenManager

VoteSpeed integrates with [TokenManager](https://www.spigotmc.org/resources/tokenmanager.8610/) to give tokens as vote rewards.

## Configuration

```yaml
# config.yml
hooks:
  tokenmanager:
    enabled: true
```

## Syntax

```
[tokens] <amount>
```

## Example: Vote Reward

```yaml
# rewards.yml
rewards:
  token-bonus:
    commands:
      - "[tokens] 50"
    player-message: "&aYou received &e50 Tokens&a!"
    chance: 100
```

## Example: Shop Item

```yaml
# shop.yml
shop-items:
  token-pack:
    slot: 14
    material: SUNFLOWER
    name: "&eToken Pack"
    lore:
      - "&7100 Tokens"
      - "&7Price: &6%price% Points"
    price: 15
    commands:
      - "[tokens] 100"
```

## Notes

- TokenManager must be installed and loaded before VoteSpeed
- If TokenManager is not installed, `[tokens]` commands are silently skipped
