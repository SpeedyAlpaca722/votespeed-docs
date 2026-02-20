# Permissions

## Player Permissions

| Permission | Description | Default |
|---|---|---|
| `votespeed.vote` | Access to `/vote`, `/vote help`, `/vote rewards`, `/vote history` | Everyone |
| `votespeed.gui` | Open the Vote GUI (`/vote gui`) | Everyone |
| `votespeed.stats` | View own vote stats (`/vote stats`) | Everyone |
| `votespeed.stats.other` | View other players' stats (`/vote stats <player>`) | OP only |
| `votespeed.top` | View top voters (`/vote top`) | Everyone |
| `votespeed.next` | Check vote cooldowns (`/vote next`) | Everyone |
| `votespeed.points` | View vote points (`/vote points`) | Everyone |
| `votespeed.shop` | Open the Vote Shop (`/vote shop`) | Everyone |
| `votespeed.toggle` | Toggle vote broadcasts (`/vote toggle`) | Everyone |
| `votespeed.party` | View VoteParty progress (`/vote party`) | Everyone |

## Admin Permissions

| Permission | Description | Default |
|---|---|---|
| `votespeed.admin` | Access to all `/vote admin` commands | OP only |

The `votespeed.admin` permission grants access to:

- `/vote admin reload`
- `/vote admin debug`
- `/vote admin simulate`
- `/vote admin setpoints` / `addpoints` / `removepoints`
- `/vote admin setvotes`
- `/vote admin setstreak`
- `/vote admin reset` / `resetall`
- `/vote admin info`

## Notification Permissions

| Permission | Description | Default |
|---|---|---|
| `votespeed.admin` | Receive update notifications on join | OP only |

## Using with LuckPerms

### Grant all player permissions

All player permissions are granted by default. To restrict access:

```
/lp group default permission set votespeed.shop false
```

### Grant admin access

```
/lp user Steve permission set votespeed.admin true
```

### Grant stats viewing for moderators

```
/lp group moderator permission set votespeed.stats.other true
```

## Proxy Permissions

On BungeeCord/Velocity, use the `admin-players` config option:

```yaml
# Proxy config.yml
admin-players: ["TRySpeedy", "Admin2"]
```

Or use a proxy-compatible permissions plugin like LuckPerms.
