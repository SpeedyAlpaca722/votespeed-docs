# Quick Start

This guide walks you through setting up VoteSpeed from scratch in under 10 minutes.

## 1. Install VoteSpeed

1. Download the correct JAR for your server (see [Installation](installation.md))
2. Place it in your `plugins/` folder
3. Restart your server
4. Verify VoteSpeed loaded: check the console for `VoteSpeed v1.0.0 enabled`

## 2. Set Your Language

Open `plugins/VoteSpeed/config.yml`:

```yaml
# en = English, de = German
language: en
```

Reload with `/vote admin reload`.

## 3. Add Your Vote Sites

Open `plugins/VoteSpeed/sites.yml` and fill in your vote URLs:

```yaml
sites:
  - serviceName: "TopG"
    displayName: "&eTopG"
    voteUrl: "https://topg.org/minecraft-servers/your-server/vote"
    cooldown-hours: 24

  - serviceName: "PlanetMinecraft"
    displayName: "&aPlanet MC"
    voteUrl: "https://planetminecraft.com/server/your-server/vote"
    cooldown-hours: 24
```

> **Important:** The `serviceName` must match exactly what the vote site sends. Most sites send their name (e.g., "TopG", "PlanetMinecraft"). Check your vote site's documentation.

> Only sites with a non-empty `voteUrl` will appear in the GUI and `/vote` command.

## 4. Configure Your Vote Site

On your server listing website:

1. Go to your server's Votifier settings
2. Enter your **server IP** as the Votifier IP
3. Enter **8192** as the Votifier port (or check `config.yml` → `receiver.port`)
4. Copy the token from `config.yml` → `receiver.tokens.default` and paste it

## 5. Test It

1. Run `/vote admin simulate YourName TopG` to simulate a test vote
2. You should see vote confirmation messages and receive rewards
3. Try `/vote gui` to see the vote GUI
4. Try `/vote shop` to see the vote shop

## 6. Customize Rewards

Open `plugins/VoteSpeed/rewards.yml`:

```yaml
rewards:
  default:
    commands:
      - "give %player% diamond 1"
      - "[money] 100"
    player-message: "&aYou received &e1 Diamond &a+ &e100$&a!"
    chance: 100
```

See [Rewards Configuration](../configuration/rewards.md) for the full reward system guide.

## What's Next?

- [Configure the Vote Shop](../configuration/shop.md) — Set up shop items players can buy with vote points
- [Set up VoteParty](../features/voteparty.md) — Reward all players when a vote goal is reached
- [Add Integrations](../integrations/economy.md) — Connect Vault, LuckPerms, PlaceholderAPI
- [Proxy Setup](../advanced/proxy-setup.md) — Forward votes across a BungeeCord/Velocity network
