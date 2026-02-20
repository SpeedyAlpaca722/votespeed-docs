# Installation

## Requirements

- **Java 21** or higher
- **Minecraft Server 1.21+** (Paper, Spigot, or Folia)
- A server listing account on at least one vote site (e.g., TopG, PlanetMinecraft)

## Step 1: Download the Correct JAR

Choose the JAR file that matches your server platform:

| Your Server Software | Download |
|---|---|
| **Paper** (recommended) | `VoteSpeed-1.0.0.jar` |
| **Spigot** | `VoteSpeed-Spigot-1.0.0.jar` |
| **Folia** | `VoteSpeed-Folia-1.0.0.jar` |
| **BungeeCord** (proxy only) | `VoteSpeed-Bungee-1.0.0.jar` |
| **Velocity** (proxy only) | `VoteSpeed-Velocity-1.0.0.jar` |

> **Not sure which one?** See [Choosing Your JAR](choosing-your-jar.md) for details.

## Step 2: Install the Plugin

### Standalone Server (Paper / Spigot / Folia)

1. Place the JAR file in your server's `plugins/` folder
2. Start or restart your server
3. VoteSpeed will generate all configuration files in `plugins/VoteSpeed/`

### Proxy Network (BungeeCord / Velocity)

1. Place the **proxy JAR** in the proxy's `plugins/` folder
2. Place a **backend JAR** (Paper/Spigot/Folia) in each backend server's `plugins/` folder
3. Start the proxy and backend servers
4. Configure vote forwarding — see [Proxy Setup](../advanced/proxy-setup.md)

## Step 3: Configure Vote Sites

1. Open `plugins/VoteSpeed/sites.yml`
2. Add your vote URLs for each site
3. Reload with `/vote admin reload`

See [Quick Start](quick-start.md) for a step-by-step walkthrough.

## Step 4: Configure Your Vote Site

On your server listing (e.g., TopG, PlanetMinecraft):

1. Set the **Votifier IP** to your server's IP address
2. Set the **Votifier Port** to `8192` (default, see `config.yml`)
3. Copy the **token** from `plugins/VoteSpeed/config.yml` → `receiver.tokens.default`
4. Set the token on your vote site (NuVotifier v2 token)

> **Important:** VoteSpeed has a built-in NuVotifier receiver. You do **not** need to install a separate Votifier or NuVotifier plugin.

## Generated Files

After first startup, VoteSpeed creates these files in `plugins/VoteSpeed/`:

```
plugins/VoteSpeed/
├── config.yml          # Main configuration
├── sites.yml           # Vote site definitions
├── shop.yml            # Vote shop items
├── gui.yml             # Vote GUI layout
├── rewards.yml         # Vote reward definitions
├── lang/
│   ├── en.yml          # English messages
│   └── de.yml          # German messages
└── votes.db            # SQLite database (if using SQLite)
```

## Optional Dependencies

VoteSpeed works standalone, but supports these optional plugins:

| Plugin | Purpose |
|---|---|
| [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) | Placeholders in other plugins |
| [Vault](https://www.spigotmc.org/resources/vault.34315/) / [VaultUnlocked](https://github.com/TheNewEconomy/VaultUnlocked) | Economy support for money rewards |
| [LuckPerms](https://luckperms.net/) | Temporary ranks/permissions as rewards |
| [Floodgate](https://geysermc.org/) | Bedrock player support with native forms |
| [CrazyCrates](https://www.spigotmc.org/resources/crazycrates.17599/) | Crate keys as rewards |
| [ItemsAdder](https://www.spigotmc.org/resources/itemsadder.73355/) | Custom items in GUIs |
| [Oraxen](https://www.spigotmc.org/resources/oraxen.72448/) | Custom items in GUIs |

None of these are required. VoteSpeed detects them automatically at startup.
