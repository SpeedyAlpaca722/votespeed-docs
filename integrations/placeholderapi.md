# PlaceholderAPI

VoteSpeed integrates with [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) to provide vote-related placeholders for use in other plugins (scoreboards, tab lists, holograms, etc.).

## Setup

1. Install PlaceholderAPI on your server
2. VoteSpeed registers its placeholders automatically — no `/papi ecloud` download needed

## Available Placeholders

| Placeholder | Description | Example Output |
|---|---|---|
| `%votespeed_total%` | Total votes | `42` |
| `%votespeed_streak%` | Current streak | `7` |
| `%votespeed_best_streak%` | Best streak ever | `14` |
| `%votespeed_points%` | Vote points balance | `42` |
| `%votespeed_daily%` | Votes today | `3` |
| `%votespeed_weekly%` | Votes this week | `12` |
| `%votespeed_monthly%` | Votes this month | `42` |
| `%votespeed_party_current%` | VoteParty current count | `37` |
| `%votespeed_party_needed%` | VoteParty votes needed | `50` |
| `%votespeed_last_vote%` | Last vote timestamp | `2024-01-15 14:30` |

## Usage Examples

### Scoreboard (e.g., with TAB or AnimatedScoreboard)

```
&7Votes: &6%votespeed_total%
&7Streak: &6%votespeed_streak%
&7Points: &6%votespeed_points%
```

### Tab List (e.g., with TAB plugin)

```
&7[&6%votespeed_streak%🔥&7]
```

### Hologram (e.g., with DecentHolograms)

```
&6&lVote Leaderboard
&7VoteParty: &6%votespeed_party_current%&7/&6%votespeed_party_needed%
```

## Disabling

The PlaceholderAPI hook is automatically enabled when PlaceholderAPI is detected. To disable it, ensure PlaceholderAPI is not installed, or disable the integration in the hooks section if available.
