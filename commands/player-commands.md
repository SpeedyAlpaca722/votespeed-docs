# Player Commands

All player commands use the `/vote` base command.

## Command Overview

| Command | Description | Permission |
|---|---|---|
| `/vote` | Shows vote site links | `votespeed.vote` |
| `/vote help` | Shows the help menu | `votespeed.vote` |
| `/vote gui` | Opens the Vote GUI | `votespeed.gui` |
| `/vote shop` | Opens the Vote Shop | `votespeed.shop` |
| `/vote stats [player]` | View vote statistics | `votespeed.stats` |
| `/vote top <period> [page]` | View top voters leaderboard | `votespeed.top` |
| `/vote next` | Shows when you can vote again | `votespeed.next` |
| `/vote points` | Shows your vote point balance | `votespeed.points` |
| `/vote party` | Shows VoteParty progress | `votespeed.party` |
| `/vote toggle` | Toggle vote broadcast messages | `votespeed.toggle` |
| `/vote rewards` | Shows possible vote rewards | `votespeed.vote` |
| `/vote history` | Shows your vote history | `votespeed.vote` |

## Detailed Usage

### /vote

Shows all active vote sites with clickable links:

```
--- Vote Sites ---
TopG: https://topg.org/...
Planet MC: https://planetminecraft.com/...
```

### /vote gui

Opens a chest GUI with all vote sites. Clicking a site sends the vote URL to the player's chat. Bedrock players see a native Bedrock Form instead.

### /vote shop

Opens the vote shop GUI where players can spend their vote points. See [Vote Shop](../configuration/shop.md).

### /vote stats [player]

Shows vote statistics for yourself or another player:

```
Your stats: 42 total | Streak: 7 | Best: 14 | Points: 42
Last vote: 2024-01-15 14:30
  - TopG: 20 Votes
  - PlanetMinecraft: 22 Votes
```

Viewing other players' stats requires `votespeed.stats.other` permission.

### /vote top \<period> [page]

Shows the vote leaderboard for a specific time period:

| Period | Description |
|---|---|
| `daily` | Today |
| `weekly` | This week |
| `monthly` | This month |
| `lastmonth` | Last month |
| `all` | All time |

Example: `/vote top weekly 2` — page 2 of this week's top voters.

### /vote next

Shows the cooldown status for each vote site:

```
--- Next Votes ---
+ TopG - Vote now!
- Planet MC - Available in 2h 15m
+ MC-Servers.org - Vote now!
```

### /vote points

Shows your current vote point balance:

```
Your vote points: 42
```

### /vote party

Shows the current VoteParty progress:

```
VoteParty progress: 37/50
```

### /vote toggle

Toggles whether you receive vote broadcast messages from other players voting. Your own vote messages are always shown.

### /vote rewards

Lists all configured rewards and their chances:

```
--- Vote Rewards ---
[Normal] default - Chance: 100%
[Random] lucky - Chance: 10%
```

### /vote history

Shows your personal vote history breakdown:

```
--- Your Vote History ---
Total: 42 Votes
Today: 3 Votes
This week: 12 Votes
This month: 42 Votes
Streak: 7 days (Best: 14)
Per site:
  - TopG: 20
  - PlanetMinecraft: 22
```
