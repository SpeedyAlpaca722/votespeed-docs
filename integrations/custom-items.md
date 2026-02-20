# Custom Item Plugins

VoteSpeed supports custom items from popular resource pack / custom item plugins in its GUIs (Vote GUI and Vote Shop).

## Supported Plugins

| Plugin | Format | Config Toggle |
|---|---|---|
| [ItemsAdder](https://www.spigotmc.org/resources/itemsadder.73355/) | `itemsadder:<namespace:id>` | `hooks.itemsadder` |
| [Oraxen](https://www.spigotmc.org/resources/oraxen.72448/) | `oraxen:<id>` | `hooks.oraxen` |
| [Nexo](https://www.spigotmc.org/resources/nexo.94901/) | `nexo:<id>` | `hooks.nexo` |

## Configuration

```yaml
# config.yml
hooks:
  itemsadder:
    enabled: true
  oraxen:
    enabled: true
  nexo:
    enabled: true
```

## Usage

Use the `custom-item` field in `gui.yml` or `shop.yml`:

### Vote GUI - Site Override

```yaml
# gui.yml
vote-gui:
  site-overrides:
    TopG:
      custom-item: "oraxen:vote_emerald"
```

### Vote GUI - Filler Item

```yaml
# gui.yml
vote-gui:
  fill-empty:
    enabled: true
    custom-item: "itemsadder:my_namespace:glass_pane"
```

### Shop Item

```yaml
# shop.yml
shop-items:
  custom-sword:
    slot: 16
    custom-item: "nexo:custom_diamond_sword"
    name: "&cCustom Sword"
    lore:
      - "&7A custom sword"
      - "&7Price: &6%price% Points"
    price: 50
    commands:
      - "iagive %player% my_namespace:my_sword 1"
```

## Custom Model Data

For vanilla resource packs that use custom model data (without ItemsAdder/Oraxen/Nexo):

```yaml
# gui.yml or shop.yml
material: DIAMOND
custom-model-data: 1234
```

This sets the `CustomModelData` NBT tag on the item, which resource packs can use to display a custom texture.

## Notes

- When `custom-item` is set, it overrides the `material` field
- If the custom item plugin is not installed, the item falls back to the configured `material`
- Custom items only affect the visual display in the GUI — commands still need to handle item giving
