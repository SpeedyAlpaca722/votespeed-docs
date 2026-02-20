# Top Voters

VoteSpeed tracks vote leaderboards across multiple time periods, letting players compete for the most votes.

## Viewing Leaderboards

```
/vote top <period> [page]
```

### Available Periods

| Period | Description |
|---|---|
| `daily` | Votes today |
| `weekly` | Votes this week |
| `monthly` | Votes this month |
| `lastmonth` | Votes last month |
| `all` | All-time total votes |

### Examples

```
/vote top daily          # Today's top voters
/vote top weekly         # This week's top voters
/vote top monthly 2      # This month's top voters, page 2
/vote top all            # All-time leaderboard
```

## Output Format

```
--- Top Voters (This Week) Page 1 ---
1. Steve - 14 Votes
2. Alex - 12 Votes
3. Notch - 8 Votes
```

## Reset Schedule

Leaderboards reset automatically based on your timezone and reset time:

```yaml
# config.yml
timezone: "Europe/Berlin"
reset:
  daily-reset-time: "00:00"
```

- **Daily:** Resets at the configured time each day
- **Weekly:** Resets at the configured time on Monday
- **Monthly:** Resets at the configured time on the 1st of each month
- **Last Month:** Shows the previous month's final standings
- **All-Time:** Never resets (unless manually with `/vote admin resetall`)

## Permissions

| Permission | Description |
|---|---|
| `votespeed.top` | Access to `/vote top` (default: all players) |

## Customizing Messages

In your language file:

```yaml
vote-top-header: "&6--- Top Voters (%period%) Page %page% ---"
vote-top-entry: "&e%rank%. &f%player% &8- &6%votes% Votes"
vote-top-empty: "&7No votes for this period."
```

### Period Display Names

You can customize how period names are displayed:

```yaml
period-name-daily: "Today"
period-name-weekly: "This Week"
period-name-monthly: "This Month"
period-name-lastmonth: "Last Month"
period-name-all: "All Time"
```
