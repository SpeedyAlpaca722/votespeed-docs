# Crate Plugins

VoteSpeed integrates with crate plugins to give crate keys as vote rewards.

## Supported Crate Plugins

| Plugin | Command Prefix | Config Toggle |
|---|---|---|
| [CrazyCrates](https://www.spigotmc.org/resources/crazycrates.17599/) | `[crate]` | `hooks.crazycrates` |
| [PhoenixCrates](https://www.spigotmc.org/resources/phoenixcrates.81523/) | `[phoenixcrate]` | `hooks.phoenixcrates` |

## Configuration

```yaml
# config.yml
hooks:
  crazycrates:
    enabled: true
  phoenixcrates:
    enabled: true
```

## CrazyCrates

### Syntax

```
[crate] <crate-name> <amount>
```

### Example

```yaml
# rewards.yml
rewards:
  crate-reward:
    commands:
      - "[crate] vote 1"
    player-message: "&aYou received a &eVote Crate Key&a!"
    chance: 100
```

This gives the player 1 key for the crate named `vote` in CrazyCrates.

### In the Shop

```yaml
# shop.yml
shop-items:
  crate-key:
    slot: 12
    material: TRIPWIRE_HOOK
    name: "&eCrate Key"
    lore:
      - "&71x Vote Crate Key"
      - "&7Price: &6%price% Points"
    price: 20
    commands:
      - "[crate] vote 1"
```

## PhoenixCrates

### Syntax

```
[phoenixcrate] <crate-id> <amount>
```

### Example

```yaml
rewards:
  phoenix-crate-reward:
    commands:
      - "[phoenixcrate] votecrate 1"
    player-message: "&aYou received a &ePhoenix Crate Key&a!"
    chance: 100
```

## Notes

- The crate name/ID must match exactly what's configured in your crate plugin
- VoteSpeed uses the respective plugin's API directly for reliability
- If the crate plugin is not installed, the `[crate]` or `[phoenixcrate]` commands are silently skipped
