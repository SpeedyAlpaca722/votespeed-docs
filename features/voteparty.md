# VoteParty

VoteParty is a server-wide event that triggers when a collective vote goal is reached. When the goal is hit, **all online players** receive rewards.

## Configuration

```yaml
# config.yml
voteparty:
  enabled: true
  votes-needed: 50
  reset-after-party: true
```

| Option | Description | Default |
|---|---|---|
| `enabled` | Enable VoteParty | `true` |
| `votes-needed` | Total votes needed to trigger the party | `50` |
| `reset-after-party` | Reset the vote counter after a party triggers | `true` |

## VoteParty Rewards

VoteParty rewards are defined separately in `rewards.yml` and given to **all online players**:

```yaml
# rewards.yml
voteparty-rewards:
  commands:
    - "give %player% golden_apple 5"
    - "eco give %player% 500"
  player-message: "&d&lVOTEPARTY! &aYou received party rewards!"
```

The `%player%` placeholder is replaced with each online player's name.

## Checking Progress

Players can check VoteParty progress with:

```
/vote party
```

Output: `VoteParty progress: 37/50`

## How It Works

1. Every vote increments the global VoteParty counter
2. When the counter reaches `votes-needed`, the party triggers
3. All online players receive the configured rewards
4. A broadcast message is sent to the server
5. If `reset-after-party: true`, the counter resets to 0

## Broadcast Message

The party trigger broadcast is configured in the language file:

```yaml
# lang/en.yml
vote-party-broadcast: "&d&lVOTEPARTY! &6%current%/%needed% &7votes reached! Rewards for everyone!"
```

| Placeholder | Description |
|---|---|
| `%current%` | Current vote count |
| `%needed%` | Votes needed for party |
