# Placeholders Reference

This page lists all placeholders available throughout VoteSpeed.

## PlaceholderAPI Placeholders

These work in any plugin that supports PlaceholderAPI:

| Placeholder | Description | Example |
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

## Internal Placeholders

These work in VoteSpeed's own config files (rewards, messages, GUI, shop):

### Reward Commands & Messages

| Placeholder | Description |
|---|---|
| `%player%` | Player name |
| `%uuid%` | Player UUID |
| `%service%` | Vote site service name |
| `%streak%` | Current streak |
| `%bestStreak%` | Best streak |
| `%totalVotes%` | Total votes |
| `%dayVotes%` | Votes today |
| `%weekVotes%` | Votes this week |
| `%monthVotes%` | Votes this month |
| `%points%` | Vote points |

### GUI (gui.yml)

| Placeholder | Where | Description |
|---|---|---|
| `%name%` | Site template lore | Site display name |
| `%vote_status%` | Site template lore | "Available" or cooldown time |
| `%totalVotes%` | Info item | Total votes |
| `%streak%` | Info item | Current streak |
| `%points%` | Info item | Vote points |

### Shop (shop.yml)

| Placeholder | Where | Description |
|---|---|---|
| `%price%` | Item lore | Item's point cost |
| `%points%` | Item lore | Player's point balance |
| `%player%` | Item commands | Player name |

### Language Messages

| Placeholder | Used In | Description |
|---|---|---|
| `%player%` | Various | Player name |
| `%service%` | Vote messages | Vote site name |
| `%streak%` | Stats, rewards | Current streak |
| `%bestStreak%` | Stats | Best streak |
| `%totalVotes%` | Stats, history | Total votes |
| `%dailyVotes%` | History | Today's votes |
| `%weeklyVotes%` | History | This week's votes |
| `%monthlyVotes%` | History | This month's votes |
| `%points%` | Points, shop | Point balance |
| `%price%` | Shop | Item price |
| `%item%` | Shop | Item name |
| `%count%` | Reminders | Available site count |
| `%current%` / `%needed%` | VoteParty | Party progress |
| `%period%` / `%page%` | Top voters | Period name and page |
| `%rank%` / `%votes%` | Top voters | Rank and vote count |
| `%time%` | Cooldown | Time remaining |
| `%url%` | GUI click | Vote URL |
| `%version%` | Update | New version number |
