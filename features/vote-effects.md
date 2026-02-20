# Vote Effects

When a player votes, VoteSpeed can display various effects to celebrate the vote.

## Configuration

```yaml
# config.yml
effects:
  broadcast:
    enabled: true
  actionbar:
    enabled: true
    message: "&a+1 Vote! Streak: %streak%"
  title:
    enabled: true
    title: "&6Thank you!"
    subtitle: "&eYou voted on %service%!"
    fade-in: 10
    stay: 40
    fade-out: 10
  sound:
    enabled: true
    name: "ENTITY_PLAYER_LEVELUP"
    volume: 1.0
    pitch: 1.0
```

## Broadcast

Sends a message to all online players when someone votes:

```yaml
broadcast:
  enabled: true
```

The broadcast message is defined in the language file:

```yaml
vote-broadcast: "&e%player% &7voted on &b%service%&7! &8(&6%totalVotes% &7total)"
```

Players can toggle broadcasts with `/vote toggle` (requires `votespeed.toggle` permission).

## Action Bar

Shows a temporary message above the player's hotbar:

```yaml
actionbar:
  enabled: true
  message: "&a+1 Vote! Streak: %streak%"
```

| Placeholder | Description |
|---|---|
| `%streak%` | Current vote streak |
| `%service%` | Vote site name |

## Title

Shows a large title and subtitle on the player's screen:

```yaml
title:
  enabled: true
  title: "&6Thank you!"
  subtitle: "&eYou voted on %service%!"
  fade-in: 10
  stay: 40
  fade-out: 10
```

| Option | Description |
|---|---|
| `title` | Large text on screen |
| `subtitle` | Smaller text below the title |
| `fade-in` | Fade-in duration (ticks, 20 = 1 second) |
| `stay` | Display duration (ticks) |
| `fade-out` | Fade-out duration (ticks) |

## Sound

Plays a sound to the voting player:

```yaml
sound:
  enabled: true
  name: "ENTITY_PLAYER_LEVELUP"
  volume: 1.0
  pitch: 1.0
```

| Option | Description |
|---|---|
| `name` | Minecraft sound name (e.g., `ENTITY_PLAYER_LEVELUP`, `ENTITY_EXPERIENCE_ORB_PICKUP`) |
| `volume` | Sound volume (0.0 - 1.0) |
| `pitch` | Sound pitch (0.5 - 2.0, where 1.0 = normal) |

You can find all sound names in the [Minecraft Wiki](https://minecraft.wiki/w/Sounds.json) or by using tab completion in-game.

## Disabling Individual Effects

Set `enabled: false` for any effect you don't want:

```yaml
effects:
  broadcast:
    enabled: false    # No broadcast
  actionbar:
    enabled: true     # Keep actionbar
  title:
    enabled: false    # No title
  sound:
    enabled: true     # Keep sound
```
