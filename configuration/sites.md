# Vote Sites (sites.yml)

This file defines all voting sites your server is listed on. Each site appears in the Vote GUI and `/vote` command.

**Location:** `plugins/VoteSpeed/sites.yml`

## Structure

```yaml
sites:
  - serviceName: "TopG"
    displayName: "&eTopG"
    voteUrl: "https://topg.org/minecraft-servers/your-server/vote"
    cooldown-hours: 24
```

## Options Per Site

| Option | Description | Required |
|---|---|---|
| `serviceName` | Internal identifier. **Must match** the service name sent by the vote site. | Yes |
| `displayName` | Display name shown in the GUI and messages. Supports `&` color codes. | Yes |
| `voteUrl` | The voting URL. Players are sent this link when they click in the GUI. | Yes |
| `cooldown-hours` | Hours between votes on this site (used by `/vote next`). | Yes |

## Important Rules

- **`serviceName` must match exactly** what the vote site sends as the service name. Most sites use their name (e.g., `"TopG"`, `"PlanetMinecraft"`). Check your vote site's Votifier documentation.
- **Only sites with a non-empty `voteUrl`** are shown in the GUI and `/vote` list. Set `voteUrl: ""` to hide a site.
- Sites are displayed in the GUI in the order they appear in this file.

## Pre-Configured Sites

VoteSpeed ships with these sites pre-configured (URLs empty by default):

| Service Name | Site | Link Format |
|---|---|---|
| `TopG` | [topg.org](https://topg.org) | Dashboard → Voting Code → Simple Link |
| `MinecraftServerList` | [minecraft-server-list.com](https://minecraft-server-list.com) | Edit Server → Voting Link |
| `PlanetMinecraft` | [planetminecraft.com](https://planetminecraft.com) | Manage Server → Vote Link |
| `MinecraftServers` | [minecraftservers.org](https://minecraftservers.org) | Edit Server → Vote URL |
| `MinecraftMP` | [minecraft-mp.com](https://minecraft-mp.com) | Edit Server → Vote Link |
| `ServerPact` | [serverpact.com](https://serverpact.com) | Edit Server → Vote Link |
| `TrackyServer` | [trackyserver.com](https://trackyserver.com) | Edit Server → Vote URL |
| `MinecraftServerEU` | [minecraft-server.eu](https://minecraft-server.eu) | Edit Server → Vote Link |
| `BestMCServers` | [best-minecraft-servers.co](https://best-minecraft-servers.co) | Edit Server → Vote URL |

## Adding a New Site

To add a site not in the default list:

```yaml
sites:
  # ... existing sites ...

  - serviceName: "MyCustomSite"
    displayName: "&dMy Custom Site"
    voteUrl: "https://example.com/vote/my-server"
    cooldown-hours: 12
```

## Hiding a Site

To temporarily hide a site without deleting it, set the URL to empty:

```yaml
  - serviceName: "TopG"
    displayName: "&eTopG"
    voteUrl: ""           # <-- Empty = hidden from GUI and /vote
    cooldown-hours: 24
```

The site will still process incoming votes, but it won't appear in the GUI.

## Finding Your Service Name

If votes aren't being matched to the correct site, enable debug mode to see what service name is being sent:

```yaml
# In config.yml
receiver:
  debug: true
```

Then vote and check the console. You'll see a log entry like:

```
[VoteSpeed] [DEBUG] Vote received: player=Steve, service=TopG
```

Use that exact `service` value as your `serviceName`.
