# Economy (Vault / VaultUnlocked)

VoteSpeed integrates with economy plugins through Vault v1 and VaultUnlocked v2 APIs, allowing you to give or require money as part of vote rewards and shop purchases.

## Supported Economy Plugins

Any economy plugin that hooks into Vault or VaultUnlocked works with VoteSpeed, including:

- EssentialsX Economy
- CMI Economy
- TheNewEconomy
- PlayerPoints
- And many more

## Configuration

```yaml
# config.yml
hooks:
  economy:
    enabled: true
    provider: auto
```

| Option | Description |
|---|---|
| `enabled` | Enable/disable economy integration |
| `provider` | `auto` = detect automatically (VaultUnlocked preferred), `vault` = force Vault v1, `vaultunlocked` = force VaultUnlocked v2 |

## Using Money in Rewards

Use the `[money]` command prefix to deposit money directly:

```yaml
# rewards.yml
rewards:
  default:
    commands:
      - "give %player% diamond 1"
      - "[money] 100"
    player-message: "&aYou received 1 Diamond + $100!"
    chance: 100
```

The `[money]` prefix uses the Vault/VaultUnlocked API directly — no need for the `eco give` command.

## Money Cost in Shop

Shop items can require money in addition to vote points:

```yaml
# shop.yml
shop-items:
  money-boost:
    slot: 14
    material: GOLD_INGOT
    name: "&6Money Boost"
    lore:
      - "&71000$ Ingame money"
      - "&7Price: &6%price% Points &7+ &6500$"
    price: 10
    money-price: 500.0
    commands:
      - "eco give %player% 1000"
```

The player must have both enough vote points AND enough money to purchase the item.

## Vault v1 vs VaultUnlocked v2

| Feature | Vault v1 | VaultUnlocked v2 |
|---|---|---|
| API Package | `net.milkbowl.vault` | `net.milkbowl.vault2` |
| UUID Support | Limited | Full |
| Maintained | Legacy | Actively maintained |

VoteSpeed supports both. With `provider: auto`, VaultUnlocked v2 is preferred if both are available.

## Troubleshooting

- **"Not enough money" but player has money:** Ensure your economy plugin is properly hooked into Vault. Check `/vault-info` or similar.
- **Economy not detected:** Make sure Vault (or VaultUnlocked) is installed AND an economy provider plugin (e.g., EssentialsX) is also installed. Vault alone is not an economy — it's a bridge.
