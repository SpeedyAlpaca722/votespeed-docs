# Proxy Setup (BungeeCord / Velocity)

VoteSpeed supports proxy networks where the vote receiver runs on the proxy and forwards votes to backend servers.

## Architecture

```
Vote Site → Proxy (VoteSpeed-Bungee/Velocity) → Plugin Messaging → Backend Servers (VoteSpeed)
```

The proxy receives votes and forwards them to the correct backend server via plugin messaging.

## Step 1: Install JARs

| Location | JAR |
|---|---|
| Proxy `plugins/` | `VoteSpeed-Bungee-1.0.0.jar` or `VoteSpeed-Velocity-1.0.0.jar` |
| Each backend `plugins/` | `VoteSpeed-1.0.0.jar` (Paper), `VoteSpeed-Spigot-1.0.0.jar`, or `VoteSpeed-Folia-1.0.0.jar` |

## Step 2: Configure the Proxy

After first start, edit the proxy's `plugins/VoteSpeed/config.yml`:

```yaml
# Proxy config.yml
language: en

receiver:
  host: "0.0.0.0"
  port: 8192
  auto-port-finder: true
  disable-v1-protocol: false
  debug: false
  tokens:
    default: "YOUR_TOKEN_HERE"

forwarding:
  enabled: true
  method: "player"          # "player" or "all"
  channel: "votespeed:vote"
  proxy-processing: false
```

### Forwarding Methods

| Method | Description |
|---|---|
| `player` | Forward the vote only to the server the player is currently on |
| `all` | Forward the vote to all connected backend servers |

> **Recommendation:** Use `player` for most setups. Use `all` only if you need all servers to process every vote (e.g., for syncing).

## Step 3: Configure Backend Servers

On each backend server, edit `plugins/VoteSpeed/config.yml`:

```yaml
# Backend config.yml
forwarding:
  method: pluginMessaging
  pluginMessaging:
    channel: "votespeed:vote"
```

> **Important:** The `channel` must match between proxy and backend configs.

### Disable the Backend Receiver

When using a proxy, the backend servers should **not** run their own Votifier receiver. The proxy handles vote reception. You can keep the receiver enabled as a fallback, but make sure the port doesn't conflict.

## Step 4: Configure Vote Sites

On your vote site listings, point the Votifier settings to your **proxy**:

- **IP:** Your proxy's public IP
- **Port:** `8192` (or whatever you set in the proxy's `receiver.port`)
- **Token:** The token from the proxy's `config.yml`

## Proxy Security Settings

The proxy config includes additional security options:

```yaml
security:
  rate-limit:
    enabled: true
    max-per-minute: 20
    burst-size: 5
  ip-whitelist:
    enabled: false
    ips: []
  replay-protection:
    enabled: true
    window-seconds: 60
  max-concurrent-connections: 50
  connection-timeout-seconds: 10
```

| Option | Description |
|---|---|
| `rate-limit` | Limits incoming votes per minute to prevent abuse |
| `ip-whitelist` | Only accept votes from specific IPs (supports wildcards and CIDR) |
| `replay-protection` | Prevents replayed vote packets within a time window |
| `max-concurrent-connections` | Maximum simultaneous connections to the receiver |
| `connection-timeout-seconds` | Timeout for inactive connections |

### IP Whitelist Example

```yaml
ip-whitelist:
  enabled: true
  ips:
    - "192.168.1.*"
    - "10.0.0.0/24"
    - "203.0.113.42"
```

## Proxy Commands

See [Proxy Commands](../commands/proxy-commands.md) for available commands on the proxy.

## Troubleshooting

### Votes not being forwarded

1. Enable debug mode on the proxy: `/bvote debug`
2. Check the proxy console for incoming vote logs
3. Verify the `channel` matches between proxy and backend configs
4. Ensure `forwarding.method` is set to `pluginMessaging` on backend servers

### Player not found on any server

If `forwarding.method: player` and the player is offline, the vote is not forwarded. Consider using `method: all` if backend servers should process offline votes.

### Port conflicts

If you have multiple servers, each Votifier receiver needs a unique port. On a proxy setup, only the proxy receiver needs to be accessible from the internet.
