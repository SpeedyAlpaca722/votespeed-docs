# Language Files

VoteSpeed supports multiple languages. All player-facing messages are defined in language files that can be fully customized.

**Location:** `plugins/VoteSpeed/lang/`

## Selecting a Language

In `config.yml`:

```yaml
language: en
```

| Value | Language |
|---|---|
| `en` | English |
| `de` | German |

## File Structure

```
plugins/VoteSpeed/lang/
├── en.yml    # English messages
└── de.yml    # German messages
```

## Creating a Custom Language

1. Copy `en.yml` (or `de.yml`) and rename it (e.g., `fr.yml`)
2. Translate all messages in the new file
3. Set `language: fr` in `config.yml`
4. Reload with `/vote admin reload`

## Message Format

All messages support Minecraft `&` color codes:

| Code | Color | Code | Format |
|---|---|---|---|
| `&0` | Black | `&l` | **Bold** |
| `&1` | Dark Blue | `&m` | ~~Strikethrough~~ |
| `&2` | Dark Green | `&n` | Underline |
| `&3` | Dark Aqua | `&o` | *Italic* |
| `&4` | Dark Red | `&r` | Reset |
| `&5` | Dark Purple | `&k` | Obfuscated |
| `&6` | Gold | | |
| `&7` | Gray | | |
| `&8` | Dark Gray | | |
| `&9` | Blue | | |
| `&a` | Green | | |
| `&b` | Aqua | | |
| `&c` | Red | | |
| `&d` | Light Purple | | |
| `&e` | Yellow | | |
| `&f` | White | | |

## Key Reference

### General

| Key | Description |
|---|---|
| `prefix` | Message prefix shown before most messages |
| `no-permission` | Shown when player lacks permission |
| `feature-disabled` | Shown when a disabled feature is used |
| `player-only` | Shown when a player-only command is used from console |
| `player-not-found` | Shown when a specified player doesn't exist |

### Vote Messages

| Key | Description | Placeholders |
|---|---|---|
| `vote-received` | Sent to the player on vote | `%player%`, `%streak%`, `%points%` |
| `vote-broadcast` | Broadcast to all players | `%player%`, `%service%`, `%totalVotes%` |
| `vote-sites-header` | Header for `/vote` site list | — |
| `vote-site-entry` | Each site in `/vote` list | `%name%`, `%url%` |

### Stats & History

| Key | Description | Placeholders |
|---|---|---|
| `vote-stats` | Own stats output | `%totalVotes%`, `%streak%`, `%bestStreak%`, `%points%` |
| `vote-stats-other` | Other player's stats | `%player%`, `%totalVotes%`, `%streak%`, `%points%` |
| `vote-history-header` | Vote history header | — |
| `vote-history-total` | Total votes line | `%totalVotes%` |
| `vote-history-daily` | Today's votes | `%dailyVotes%` |
| `vote-history-weekly` | This week's votes | `%weeklyVotes%` |
| `vote-history-monthly` | This month's votes | `%monthlyVotes%` |
| `vote-history-streak` | Streak info | `%streak%`, `%bestStreak%` |

### Top Voters

| Key | Description | Placeholders |
|---|---|---|
| `vote-top-header` | Leaderboard header | `%period%`, `%page%` |
| `vote-top-entry` | Each leaderboard entry | `%rank%`, `%player%`, `%votes%` |
| `vote-top-empty` | No votes for period | — |
| `period-name-daily` | "Today" | — |
| `period-name-weekly` | "This Week" | — |
| `period-name-monthly` | "This Month" | — |
| `period-name-lastmonth` | "Last Month" | — |
| `period-name-all` | "All Time" | — |

### Vote Shop

| Key | Description | Placeholders |
|---|---|---|
| `vote-points-balance` | Points balance message | `%points%` |
| `vote-shop-bought` | Successful purchase | `%item%`, `%price%`, `%points%` |
| `vote-shop-not-enough` | Not enough points | `%price%`, `%points%` |
| `vote-shop-not-enough-money` | Not enough money | — |

### Bedrock Forms

| Key | Description | Placeholders |
|---|---|---|
| `bedrock-shop-points-display` | Points display in Bedrock shop | `%points%` |
| `bedrock-shop-confirm-title` | Purchase confirmation title | — |
| `bedrock-shop-confirm-content` | Confirmation dialog text | `%item%`, `%price%`, `%points%` |
| `bedrock-shop-confirm-yes` | Confirm button text | — |
| `bedrock-shop-confirm-no` | Cancel button text | — |
| `bedrock-shop-price-points` | Price format (points only) | `%price%` |
| `bedrock-shop-price-points-money` | Price format (points + money) | `%price%`, `%money%` |

### VoteParty

| Key | Description | Placeholders |
|---|---|---|
| `vote-party-broadcast` | Party trigger broadcast | `%current%`, `%needed%` |
| `vote-party-progress` | Party progress display | `%current%`, `%needed%` |

### Reminders

| Key | Description | Placeholders |
|---|---|---|
| `vote-reminder-login` | Login reminder | `%count%` |
| `vote-reminder-periodic` | Periodic reminder | — |

### GUI

| Key | Description | Placeholders |
|---|---|---|
| `gui-vote-status-available` | Vote available status text | — |
| `gui-vote-status-cooldown` | Vote cooldown status text | `%time%` |
| `gui-click-to-vote` | Click-to-vote message in chat | `%url%` |

## Proxy Language Files

BungeeCord and Velocity have their own separate language files with proxy-specific messages. These are located in the proxy plugin's config folder.
