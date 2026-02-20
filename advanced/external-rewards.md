# External Reward Files

VoteSpeed can load additional reward definitions from separate YAML files, letting you organize complex reward setups without cluttering the main `rewards.yml`.

## Configuration

```yaml
# rewards.yml
external-reward-files: true
```

When enabled, VoteSpeed scans the `plugins/VoteSpeed/rewards/` directory for additional `.yml` files.

## Directory Structure

```
plugins/VoteSpeed/
├── rewards.yml              # Main reward file (always loaded)
└── rewards/                 # External reward files (optional)
    ├── streak-rewards.yml
    ├── milestone-rewards.yml
    └── seasonal-event.yml
```

## File Format

External reward files use the same format as the `rewards` section in `rewards.yml`:

```yaml
# rewards/streak-rewards.yml
streak-3day:
  condition:
    min-streak: 3
  commands:
    - "give %player% golden_apple 3"
  player-message: "&63-day streak! &e3 Golden Apples!"
  chance: 100

streak-7day:
  condition:
    min-streak: 7
  commands:
    - "[luckperms] group vip 24h"
  player-message: "&6&l7-day streak! &eVIP for 24h!"
  chance: 100
```

## Use Cases

- **Seasonal events:** Add/remove a reward file for holiday events without touching the main config
- **Per-site rewards:** Organize rewards by vote site
- **Complex setups:** Keep milestone, streak, and random rewards in separate files for clarity

## Notes

- All external rewards are processed in addition to rewards in `rewards.yml`
- Reward names must be unique across all files
- Files are loaded alphabetically
- Changes require `/vote admin reload` to take effect
