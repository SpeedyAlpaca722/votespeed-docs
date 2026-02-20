# Vote GUI (gui.yml)

The Vote GUI is a chest inventory where players can see all vote sites and click to vote. It automatically loads sites from `sites.yml`.

**Location:** `plugins/VoteSpeed/gui.yml`

## Enable / Disable

```yaml
enabled: true
```

Set to `false` to completely disable the GUI. `/vote gui` will be blocked and removed from tab completion.

## GUI Settings

```yaml
vote-gui:
  title: "&6&lVote GUI"
  size: 27
  fill-empty:
    enabled: true
    material: GRAY_STAINED_GLASS_PANE
    name: " "
    custom-model-data: 0
    custom-item: ""
```

| Option | Description | Default |
|---|---|---|
| `title` | GUI window title. Supports `&` color codes. | `&6&lVote GUI` |
| `size` | Inventory size (9, 18, 27, 36, 45, or 54). | `27` |
| `fill-empty.enabled` | Fill empty slots with a filler item. | `true` |
| `fill-empty.material` | Material for filler items. | `GRAY_STAINED_GLASS_PANE` |
| `fill-empty.custom-model-data` | Custom model data for the filler item. | `0` |
| `fill-empty.custom-item` | Custom item plugin reference for filler. | `""` |

## Site Template

The site template defines the default appearance for all vote site items in the GUI:

```yaml
  site-template:
    material: EMERALD
    custom-model-data: 0
    custom-item: ""
    lore:
      - "&7Click to vote on %name%!"
      - "&7Status: %vote_status%"
      - ""
      - "&eClick to open"
```

| Option | Description |
|---|---|
| `material` | Default material for vote site items |
| `lore` | Default lore template. Supports placeholders. |

### Template Placeholders

| Placeholder | Description |
|---|---|
| `%name%` | The site's display name from `sites.yml` |
| `%vote_status%` | Shows "Available" or cooldown time remaining |

## Per-Site Overrides

You can customize individual vote sites to have different materials, names, lore, or positions:

```yaml
  site-overrides:
    TopG:
      slot: 11
      material: GOLD_INGOT
      name: "&e&lTopG"
      custom-model-data: 0
      custom-item: ""
      lore:
        - "&7Vote now on TopG!"
        - "&7Status: %vote_status%"
        - ""
        - "&eClick to open"
```

### Override Options

| Option | Description | Required |
|---|---|---|
| `slot` | Fixed inventory slot. `-1` = auto-centered (default). | No |
| `material` | Override the template material. | No |
| `name` | Override the display name. | No |
| `custom-model-data` | Custom model data. | No |
| `custom-item` | Custom item from ItemsAdder/Oraxen/Nexo. | No |
| `lore` | Override the lore template. | No |

All fields are optional. Any field not set falls back to the site template.

### Custom Item Example

```yaml
    PlanetMinecraft:
      slot: 13
      custom-item: "oraxen:vote_emerald"
```

## Info Item

The info item shows player statistics in the GUI:

```yaml
  info-item:
    enabled: true
    slot: 22
    material: BOOK
    custom-model-data: 0
    custom-item: ""
    name: "&6Your Stats"
    lore:
      - "&7Votes: &6%totalVotes%"
      - "&7Streak: &6%streak%"
      - "&7Points: &6%points%"
```

### Info Item Placeholders

| Placeholder | Description |
|---|---|
| `%totalVotes%` | Player's total vote count |
| `%streak%` | Current daily vote streak |
| `%points%` | Current vote points balance |

## Auto-Centering

By default, vote site items are automatically centered in the GUI based on the number of active sites. If you want manual control, use the `slot` option in `site-overrides` to place each site at a specific position.

## Bedrock Players

Bedrock players (via Geyser/Floodgate) automatically see a native Bedrock SimpleForm instead of the chest GUI. The form includes the same information and site buttons. See [Bedrock Support](../advanced/bedrock-support.md).
