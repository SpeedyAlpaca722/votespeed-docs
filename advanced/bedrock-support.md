# Bedrock Support (Geyser / Floodgate)

VoteSpeed fully supports Bedrock Edition players connecting through [Geyser](https://geysermc.org/) and [Floodgate](https://wiki.geysermc.org/floodgate/). Bedrock players see native Bedrock Forms instead of chest GUIs.

## Requirements

- [Geyser](https://geysermc.org/) — Allows Bedrock players to connect to Java servers
- [Floodgate](https://wiki.geysermc.org/floodgate/) — Handles Bedrock player authentication (recommended, but not strictly required for detection)

## Configuration

```yaml
# config.yml
bedrock-forms:
  enabled: true
  shop-confirm-dialog: true
```

| Option | Description | Default |
|---|---|---|
| `enabled` | Enable native Bedrock Forms for Bedrock players | `true` |
| `shop-confirm-dialog` | Show a confirmation dialog before shop purchases | `true` |

## How It Works

When a Bedrock player opens the Vote GUI (`/vote gui`) or Vote Shop (`/vote shop`), VoteSpeed automatically detects they are a Bedrock player and shows a native Bedrock Form instead of a chest inventory.

### Vote GUI Form

Bedrock players see a **SimpleForm** with:
- Player stats (votes, streak, points) at the top
- One button per vote site
- Clicking a button sends the vote URL to chat

### Vote Shop Form

Bedrock players see a **SimpleForm** with:
- Current point balance at the top
- One button per shop item (showing name, description, and price)
- A **ModalForm** confirmation dialog before purchasing

## Bedrock Player Detection

VoteSpeed uses a 3-method detection system to reliably identify Bedrock players:

1. **Name Prefix** — Floodgate adds a prefix (usually `.`) to Bedrock player names
2. **UUID Format** — Floodgate generates UUIDs with a specific pattern (`00000000-0000-0000-0009-*`)
3. **Floodgate API** — Falls back to the Floodgate API if available

This means Bedrock players are detected even if the Floodgate API fails to initialize.

## Language Support

Bedrock Forms use the same language files as the rest of the plugin. All text in Bedrock Forms is configurable:

```yaml
# lang/en.yml
bedrock-shop-points-display: "&7Your Points: &6%points%"
bedrock-shop-confirm-title: "Confirm Purchase"
bedrock-shop-confirm-content: "Buy \"%item%\" for %price%?\nYour balance: %points% Points"
bedrock-shop-confirm-yes: "Confirm"
bedrock-shop-confirm-no: "Cancel"
bedrock-shop-price-points: "%price% Points"
bedrock-shop-price-points-money: "%price% Points + %money%$"
```

```yaml
# lang/de.yml
bedrock-shop-points-display: "&7Deine Punkte: &6%points%"
bedrock-shop-confirm-title: "Kauf bestätigen"
bedrock-shop-confirm-content: "\"%item%\" für %price% kaufen?\nDein Guthaben: %points% Punkte"
bedrock-shop-confirm-yes: "Bestätigen"
bedrock-shop-confirm-no: "Abbrechen"
bedrock-shop-price-points: "%price% Punkte"
bedrock-shop-price-points-money: "%price% Punkte + %money%$"
```

## Color Codes

Bedrock Forms support Minecraft `§` color codes natively. VoteSpeed automatically converts `&` color codes from your config files to `§` codes for Bedrock Forms, so your colors from `shop.yml`, `gui.yml`, and language files work seamlessly.

## Setup Guide

### 1. Install Geyser & Floodgate

Follow the [Geyser Setup Guide](https://wiki.geysermc.org/geyser/setup/) and [Floodgate Setup Guide](https://wiki.geysermc.org/floodgate/setup/).

### 2. Enable Bedrock Forms

In `config.yml`:

```yaml
bedrock-forms:
  enabled: true
```

### 3. Test

1. Connect with a Bedrock client (or use an emulator)
2. Run `/vote gui` — you should see a native Bedrock Form
3. Run `/vote shop` — you should see the shop form with a purchase confirmation

### 4. Customize

Edit the `bedrock-shop-*` keys in your language file to customize all text in the Bedrock Forms.

## Without Floodgate

If you run Geyser without Floodgate, VoteSpeed can still detect Bedrock players using the name prefix method (if your Geyser config adds a prefix to Bedrock names). However, the Floodgate API features won't be available. For the best experience, always use Floodgate alongside Geyser.
