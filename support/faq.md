# FAQ

## General

### Do I need NuVotifier or Votifier?

**No.** VoteSpeed has a built-in NuVotifier receiver. Do **not** install a separate Votifier plugin — it will conflict with VoteSpeed.

### Which JAR do I need?

See [Choosing Your JAR](../getting-started/choosing-your-jar.md). In short:
- **Paper/Purpur:** `VoteSpeed-Paper-1.0.0.jar`
- **Spigot:** `VoteSpeed-Spigot-1.0.0.jar`
- **Folia:** `VoteSpeed-Folia-1.0.0.jar`

### Does VoteSpeed work with Folia?

Yes. Use the `VoteSpeed-Folia-1.0.0.jar` which is built specifically for Folia's regionized threading model.

### Does VoteSpeed support Bedrock players?

Yes. With Geyser and Floodgate installed, Bedrock players see native Bedrock Forms instead of chest GUIs. See [Bedrock Support](../advanced/bedrock-support.md).

### Can I use VoteSpeed on a proxy network?

Yes. Install the proxy JAR on BungeeCord/Velocity and a backend JAR on each game server. See [Proxy Setup](../advanced/proxy-setup.md).

## Configuration

### How do I find the correct serviceName?

Enable debug mode in `config.yml`:

```yaml
receiver:
  debug: true
```

Then vote and check the console for: `[VoteSpeed] [DEBUG] Vote received: player=Steve, service=TopG`

Use that exact `service` value as your `serviceName` in `sites.yml`.

### How do I change the language?

In `config.yml`, set:

```yaml
language: de    # or en, or your custom language code
```

Then reload: `/vote admin reload`

### How do I add a custom language?

1. Copy `plugins/VoteSpeed/lang/en.yml` to e.g., `plugins/VoteSpeed/lang/fr.yml`
2. Translate all messages
3. Set `language: fr` in `config.yml`
4. Reload

### How do I disable a feature?

- **Vote GUI:** Set `enabled: false` in `gui.yml`
- **Vote Shop:** Set `enabled: false` in `shop.yml`
- **VoteParty:** Set `voteparty.enabled: false` in `config.yml`
- **Broadcast:** Set `effects.broadcast.enabled: false` in `config.yml`
- **Reminders:** Set `reminder.enabled: false` in `config.yml`
- **Points:** Set `points.enabled: false` in `config.yml`

## Voting

### Votes aren't being received

1. Check that your vote site has the correct IP, port, and token
2. Make sure no firewall is blocking the Votifier port (default: 8192)
3. Enable `receiver.debug: true` and check the console
4. Make sure no other plugin is using the same port
5. If on a proxy, ensure votes point to the proxy, not the backend

### Votes are received but rewards aren't given

1. Check `rewards.yml` syntax — a YAML error prevents loading
2. Enable debug mode to see reward processing
3. Verify `require-online: false` if players vote while offline
4. Check that reward commands are valid

### Duplicate votes are being processed

Enable anti-duplicate protection:

```yaml
anti-duplicate:
  enabled: true
  ignore-seconds: 300
```

### Player didn't receive offline vote rewards

Make sure `require-online: false` in `config.yml`. Offline votes are queued and delivered when the player joins.

## Shop

### Shop items aren't working

1. Verify `shop.yml` syntax is valid YAML
2. Check that the `commands` are valid server commands
3. Ensure the player has enough points (`/vote points`)
4. Check the console for errors after a purchase attempt

### "Not enough money" error

This means the item has a `money-price` set and the player's economy balance is too low. Make sure Vault and an economy plugin are installed.

## Integrations

### PlaceholderAPI placeholders showing as text

Make sure PlaceholderAPI is installed. VoteSpeed registers its expansion automatically — no eCloud download needed. Try `/papi reload` after installing.

### Vault/Economy not detected

Vault alone is not an economy. You need both:
1. **Vault** (or VaultUnlocked) — the API bridge
2. **An economy plugin** — e.g., EssentialsX, CMI, TheNewEconomy

### LuckPerms rewards not working

1. Ensure LuckPerms is installed and loaded
2. Check that the group name in `[luckperms] group vip 24h` matches an existing LuckPerms group
3. Verify the duration format is correct (e.g., `24h`, `7d`, `1w`)
