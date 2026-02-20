# Choosing Your JAR

VoteSpeed provides separate JAR files for each supported server platform. Choosing the right one ensures full compatibility and optimal performance.

## Backend Server JARs

These go into your game server's `plugins/` folder:

### VoteSpeed-Paper-1.0.0.jar (Paper)

- **For:** Paper, Purpur, and other Paper forks
- **Recommended for:** Most servers
- Paper is the most popular server software and offers the best performance and API features.

### VoteSpeed-Spigot-1.0.0.jar (Spigot)

- **For:** Spigot and CraftBukkit
- **Use when:** You specifically run Spigot and cannot use Paper
- Functionally identical to the Paper version, but without Paper-specific optimizations.

### VoteSpeed-Folia-1.0.0.jar (Folia)

- **For:** Folia (Paper's multithreaded fork)
- **Use when:** You run a Folia server
- Uses Folia's regionized thread scheduler (`EntityScheduler`, `GlobalRegionScheduler`) for full thread safety.
- **Important:** Regular Paper/Spigot JARs will **not** work on Folia.

## Proxy JARs

These go into your proxy's `plugins/` folder. You still need a backend JAR on each game server.

### VoteSpeed-Bungee-1.0.0.jar (BungeeCord)

- **For:** BungeeCord and Waterfall proxies
- Receives votes on the proxy and forwards them to backend servers via plugin messaging.

### VoteSpeed-Velocity-1.0.0.jar (Velocity)

- **For:** Velocity proxies
- Same functionality as the BungeeCord version, built for Velocity's API.

## Decision Flowchart

```
Do you use a proxy (BungeeCord/Velocity)?
├── Yes → Install proxy JAR on the proxy
│         AND a backend JAR on each game server
└── No  → Install only a backend JAR

Which server software?
├── Paper / Purpur  → VoteSpeed-Paper-1.0.0.jar
├── Spigot          → VoteSpeed-Spigot-1.0.0.jar
└── Folia           → VoteSpeed-Folia-1.0.0.jar
```

## Important Notes

- **Do not** install multiple VoteSpeed JARs on the same server
- **Do not** install the proxy JAR on a backend server (or vice versa)
- **Do not** install a separate Votifier/NuVotifier plugin — VoteSpeed has one built in
