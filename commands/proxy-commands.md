# Proxy Commands

When running VoteSpeed on a BungeeCord or Velocity proxy, additional commands are available via the `/bvote` command.

## Command Overview

| Command | Description | Permission |
|---|---|---|
| `/bvote` | Shows proxy help | `votespeed.admin` |
| `/bvote status` | Shows receiver and proxy status | `votespeed.admin` |
| `/bvote reload` | Reload proxy configuration | `votespeed.admin` |
| `/bvote debug` | Toggle debug mode | `votespeed.admin` |
| `/bvote info` | Shows server and player info | `votespeed.admin` |

## /bvote status

Displays the current status of the vote receiver and proxy:

```
--- VoteSpeed Proxy Status ---
Receiver: Active
Debug: Off
Players online: 25
Backend servers: 3
```

## /bvote debug

Toggles debug mode for the proxy receiver. When enabled, you'll see detailed logs of:

- Incoming vote connections
- Vote data received
- Forwarding to backend servers

## /bvote info

Shows information about connected backend servers:

```
--- VoteSpeed Proxy Info ---
Version: 1.0.0
Proxy type: BungeeCord
Backend servers:
  - lobby (5 players)
  - survival (15 players)
  - creative (5 players)
```

## Player Vote Command

Players on the proxy can still use `/vote` to see vote sites. The proxy synchronizes site data from backend servers.

## Permission Setup

On BungeeCord/Velocity, permissions are managed differently:

- **BungeeCord:** Use `config.yml` → `admin-players` list or a BungeeCord permissions plugin
- **Velocity:** Use LuckPerms Velocity or the `admin-players` config option

```yaml
# Proxy config.yml
admin-players: ["TRySpeedy", "Admin2"]
```
