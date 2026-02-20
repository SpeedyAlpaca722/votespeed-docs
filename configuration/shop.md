# Vote Shop (shop.yml)

The vote shop lets players exchange their vote points for items, commands, or other rewards.

**Location:** `plugins/VoteSpeed/shop.yml`

## Enable / Disable

```yaml
enabled: true
```

Set to `false` to completely disable the shop. `/vote shop` will be blocked and removed from tab completion.

## Shop GUI Settings

```yaml
shop-gui:
  title: "&6&lVote Shop"
  size: 27
  fill-empty:
    enabled: true
    material: GRAY_STAINED_GLASS_PANE
    name: " "
```

| Option | Description | Default |
|---|---|---|
| `title` | Title of the shop GUI. Supports `&` color codes. | `&6&lVote Shop` |
| `size` | Inventory size (9, 18, 27, 36, 45, or 54). Must be a multiple of 9. | `27` |
| `fill-empty.enabled` | Fill empty slots with a filler item. | `true` |
| `fill-empty.material` | Material for filler items. | `GRAY_STAINED_GLASS_PANE` |
| `fill-empty.name` | Display name for filler items (space = invisible). | `" "` |

## Shop Items

Each item under `shop-items` represents a purchasable item in the shop:

```yaml
shop-items:
  diamond-pack:
    slot: 10
    material: DIAMOND
    name: "&bDiamond Pack"
    lore:
      - "&75x Diamonds"
      - "&7Price: &6%price% Points"
      - "&7Your balance: &6%points%"
    price: 5
    commands:
      - "give %player% diamond 5"
```

### Item Options

| Option | Description | Required |
|---|---|---|
| `slot` | Inventory slot (0-53). Determines position in the GUI. | Yes |
| `material` | Minecraft material name (e.g., `DIAMOND`, `GOLD_INGOT`). | Yes |
| `name` | Display name. Supports `&` color codes. | Yes |
| `lore` | List of lore lines. Supports `&` color codes and placeholders. | Yes |
| `price` | Cost in vote points. | Yes |
| `commands` | Commands executed on purchase. `%player%` is replaced with the buyer's name. | Yes |
| `money-price` | Additional money cost via Vault (optional). | No |
| `custom-model-data` | Custom model data for resource packs (optional). | No |
| `custom-item` | Custom item from ItemsAdder, Oraxen, or Nexo (optional). | No |

### Available Placeholders (in lore)

| Placeholder | Description |
|---|---|
| `%price%` | The item's point price |
| `%points%` | The player's current point balance |

## Money + Points Pricing

You can require both vote points **and** money for an item:

```yaml
  money-boost:
    slot: 14
    material: GOLD_INGOT
    name: "&6Money Boost"
    lore:
      - "&71000$ Ingame money"
      - "&7Price: &6%price% Points &7+ &6500$"
      - "&7Your balance: &6%points%"
    price: 10
    money-price: 500.0
    commands:
      - "eco give %player% 1000"
```

This requires both 10 vote points AND $500 (via Vault/VaultUnlocked economy). If the player doesn't have enough of either, the purchase is denied.

## Custom Items

You can use custom items from supported plugins:

```yaml
  custom-sword:
    slot: 16
    custom-item: "itemsadder:my_namespace:my_sword"
    name: "&cCustom Sword"
    lore:
      - "&7A special sword"
      - "&7Price: &6%price% Points"
    price: 50
    commands:
      - "iagive %player% my_namespace:my_sword 1"
```

### Supported Custom Item Formats

| Plugin | Format |
|---|---|
| ItemsAdder | `custom-item: "itemsadder:<namespace:id>"` |
| Oraxen | `custom-item: "oraxen:<id>"` |
| Nexo | `custom-item: "nexo:<id>"` |

## Reward Command Prefixes

Shop item commands support the same special prefixes as reward commands:

| Prefix | Description | Example |
|---|---|---|
| `[money]` | Vault economy deposit | `[money] 1000` |
| `[luckperms]` | Temporary LuckPerms group/permission | `[luckperms] group vip 7d` |
| `[tokens]` | TokenManager tokens | `[tokens] 100` |
| `[crate]` | CrazyCrates key | `[crate] vote 1` |
| `[phoenixcrate]` | PhoenixCrates key | `[phoenixcrate] votecrate 1` |

## Bedrock Players

Bedrock players (via Geyser/Floodgate) automatically see a native Bedrock Form instead of the chest GUI. The form includes a purchase confirmation dialog. See [Bedrock Support](../advanced/bedrock-support.md).
