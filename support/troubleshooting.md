# Troubleshooting

## Startup Issues

### "Address already in use" error

Another plugin or process is using the Votifier port. Solutions:

1. **Remove other Votifier plugins** — VoteSpeed has its own built-in receiver
2. **Change the port** in `config.yml`:
   ```yaml
   receiver:
     port: 8193
   ```
3. **Enable auto-port-finder** (enabled by default):
   ```yaml
   receiver:
     auto-port-finder: true
   ```

### Plugin fails to load

1. Check that you're using the correct JAR for your server software
2. Verify you're running Java 21+ (`java -version`)
3. Verify you're running Minecraft 1.21+
4. Check the console for specific error messages
5. Ensure `config.yml` is valid YAML (use a [YAML validator](https://www.yamllint.com/))

### Config errors on startup

If you see "invalid configuration" errors:

1. Check your YAML syntax — common issues:
   - Missing quotes around special characters
   - Incorrect indentation (use spaces, not tabs)
   - Missing colons after keys
2. Use a YAML validator to find syntax errors
3. Delete the problematic file and restart to regenerate defaults

## Vote Issues

### Votes not being received

**Checklist:**

1. ✅ Correct IP on vote site (your server's public IP)
2. ✅ Correct port on vote site (default: `8192`)
3. ✅ Correct token on vote site (from `config.yml` → `receiver.tokens.default`)
4. ✅ Firewall allows incoming connections on the port
5. ✅ No other Votifier plugin installed
6. ✅ If on proxy: votes point to proxy IP, not backend

**Debug steps:**

```yaml
# config.yml
receiver:
  debug: true
```

Restart and vote. Check console for:
- `Received vote from...` → Vote is reaching VoteSpeed
- No log at all → Vote is not reaching the server (network/firewall issue)

### Votes received but wrong service name

The `serviceName` in `sites.yml` must match exactly what the vote site sends. Enable debug to see what's being sent:

```
[VoteSpeed] [DEBUG] Vote received: player=Steve, service=TopG
```

### Test voting

Use the simulate command to test without a real vote site:

```
/vote admin simulate YourName TopG
```

## GUI Issues

### GUI not opening

1. Check that `enabled: true` in `gui.yml` (or `shop.yml`)
2. Verify the player has the correct permission (`votespeed.gui` / `votespeed.shop`)
3. Check console for errors

### Bedrock Forms not showing

1. Verify Floodgate is installed
2. Check `bedrock-forms.enabled: true` in `config.yml`
3. Enable debug to verify Bedrock player detection
4. The player must be connecting through Geyser

### GUI items look wrong

1. Check that `material` names are valid Minecraft material names (e.g., `DIAMOND`, not `diamond`)
2. For custom items, verify the custom item plugin (ItemsAdder/Oraxen/Nexo) is installed
3. Check `gui.yml` and `shop.yml` for YAML syntax errors

## Reward Issues

### Rewards not triggering

1. Check `rewards.yml` for YAML syntax errors
2. Verify conditions are met (streak level, service name, vote count)
3. Check the `chance` value — a `chance: 10` means only 10% of votes trigger it
4. Enable debug mode to see reward processing logs

### Money rewards not working

1. Verify Vault (or VaultUnlocked) **and** an economy plugin are installed
2. Check `hooks.economy.enabled: true` in `config.yml`
3. Test manually: `eco give Steve 100` — if this fails, it's an economy plugin issue

### LuckPerms rewards not applying

1. Verify the group/permission exists in LuckPerms
2. Check the syntax: `[luckperms] group vip 24h` (note the spaces)
3. Check `hooks.luckperms.enabled: true`

## Database Issues

### MySQL connection failed

1. Verify the MySQL server is running
2. Check hostname, port, username, and password in `config.yml`
3. Ensure the database exists: `CREATE DATABASE votespeed;`
4. Verify the MySQL user has permissions on the database
5. If connecting remotely, ensure MySQL allows remote connections

### Data not persisting

1. Check for database errors in the console
2. Verify the database file (SQLite) or connection (MySQL) is working
3. Check file permissions for `votes.db` (SQLite)

## Proxy Issues

### Votes not forwarded to backend

1. Enable debug on the proxy: `/bvote debug`
2. Verify the `channel` matches between proxy and backend configs
3. Check that `forwarding.method: pluginMessaging` is set on backend servers
4. Ensure the backend VoteSpeed plugin is loaded

### Player "not found" on proxy

With `forwarding.method: player`, the player must be online. If they're offline, the vote won't be forwarded. Use `method: all` to forward to all servers regardless.

## Performance Issues

### Server lag when voting

1. Enable caching:
   ```yaml
   cache:
     enabled: true
     expiry-seconds: 60
   ```
2. Consider switching to MySQL for large player counts
3. Reduce reward complexity (fewer conditional checks)

## Getting Help

If you can't solve your issue:

1. Enable debug mode and collect the relevant console output
2. Note your server software and version
3. Note VoteSpeed version and which JAR you're using
4. Contact support on Discord: **@speedyalpaca722**
