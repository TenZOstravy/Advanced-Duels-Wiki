# Match Flow

## Countdown

When `countdown.enabled` is `true`, fighters are teleported to the arena spawns and a countdown runs (length = number of `countdown.duel.messages`). During it, movement, projectiles, PvP and interaction can each be frozen (`countdown.prevent.*`). Titles (`5…4…3…2…1…GO!`) and sounds play per message.

## During the fight

- Kits are equipped (or own inventory kept), pets removed, mcMMO skills off (per config), vanished players unvanished (Essentials).
- Protections apply per config: inventory open, item drop/pickup, command black/whitelists, teleport distance, kit-item NBT tagging.
- Timed matches (`duel.match.max-duration`, default 3 min) show a configurable boss bar in the last 2 minutes and end in a **tie** at zero.
- Leaving the server mid-duel counts as a death (and a loss).

## Winning, losing, tying

- **Death** ends 1v1 duels: winner/loser records, ratings, bets and items resolve; the winner teleports out after `teleport-delay`.
- **Team/party duels**: deaths become arena spectators; when one side is wiped, the match ends.
- **Tie** (timer, mutual end, plugin disable): money bets are refunded, no winner commands run.
- **Forfeit** (`/duel forfeit`): immediate loss with full consequences; disabled via `duel.forfeit.enabled`.
- End messages go server-wide unless `arena-only-end-message` is `true`. A firework spawns unless `spawn-firework` is off. Post-match inventories are viewable via the clickable message (`/duel inventory <uuid>`).

## Rewards & automation

Console commands can run at match start/end and separately for winner/loser:

```yaml
duel:
  match:
    start-commands: { enabled: false, commands: ['broadcast %player% is entering a duel!'] }
    end-commands:   { enabled: false, commands: ['give %winner% diamond 1'] }
    win-commands:   { enabled: false, commands: ['say %winner% won against %loser%!'] }
    lose-commands:  { enabled: false, commands: ['say %loser% lost against %winner%!'] }
```

Placeholders: `%player%` (start), `%winner%`, `%loser%`, `%kit%`, `%arena%`, `%bet_amount%` (end/win/lose). Append `{delay:ms}` to any command to delay it, e.g. `say GG!{delay:5000}`. Each group can be limited to queue matches with `queue-matches-only`.

## Cooldowns & return location

- `duel.cooldown` (seconds, default 0 = off) blocks instant re-dueling.
- Winners return to the **lobby** (`/duels setlobby`) unless `teleport-to-last-location: true` sends them back to their pre-duel spot.
- Essentials `set-back-location: true` keeps `/back` from pointing into the arena.
