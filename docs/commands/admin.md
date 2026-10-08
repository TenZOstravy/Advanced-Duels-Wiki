# Admin Commands (`/duels`)

Base permission: `duels.admin` (console-safe unless noted). Aliases: `ds`. Subcommand help is grouped: `/duels help <arena|kit|queue|sign|user|extra|arenaregen>`.

## Arenas

| Command | Description |
|---|---|
| `/duels create <name>` | Create a disabled arena |
| `/duels set <name> <1\|2>` | Set spawn point 1/2 at your location (player-only) |
| `/duels toggle <name>` | Enable/disable (flip) |
| `/duels enable <name>` / `/duels disable <name>` | Explicit on/off |
| `/duels teleport <name> [1\|2]` (aliases `tp`, `goto`) | Teleport to a spawn (player-only) |
| `/duels info <name>` | State, positions, bound kits |
| `/duels list` (alias `ls`) | Arenas, kits, queues, signs, lobby status (color-coded) |
| `/duels delete <name>` | Delete an unused arena (disable first) |
| `/duels setgroup <arena> <group>` (alias `group`) | GUI grouping |
| `/duels setarenaitem <arena>` | GUI icon = held item (player-only) |
| `/duels bind <kit>` | Arena-binding GUI for a kit (player-only) |
| `/duels wand` (alias `selectionwand`) | Arena selection wand (player-only) |

## Arena regeneration

| Command | Description |
|---|---|
| `/duels arenaregen <enable\|disable\|status> [arena]` (aliases `aregen`, `regenbounds`) | Set/check per-arena regen bounds using the wand selection |
| `/duels regen <status>` (aliases `tracker`, `blocktrack`) | Global regen system status |

See [Regeneration](../arenas/regeneration.md).

## Kits

| Command | Description |
|---|---|
| `/duels savekit <name>` | Save your inventory as a kit (player-only) |
| `/duels loadkit <name>` | Load a kit into your inventory (player-only) |
| `/duels deletekit <name>` | Delete a kit |
| `/duels setitem <kit>` | GUI icon = held item (player-only) |
| `/duels options <kit>` (alias `useoption`) | Kit characteristics GUI — Soup, UHC, Combo, Sumo, Hunger, Loka, Best-of-3 (player-only) |

## Queues & signs

| Command | Description |
|---|---|
| `/duels createqueue <name> <bet> <size> [<kit>\|-]` (alias `createq`) | Create a queue |
| `/duels deletequeue <bet> [<kit>\|-]` (aliases `delqueue`, `delq`) | Delete a queue |
| `/duels addsign <queue> <bet> <size> [<kit>\|-]` | Turn the looked-at sign into a queue sign (player-only) |
| `/duels delsign` | Remove the looked-at queue sign (player-only) |

## Players & stats

| Command | Description |
|---|---|
| `/duels edit <player> <add\|remove\|set> <wins\|losses> <amount>` | Correct win/loss records |
| `/duels reset <player>` | Wipe all stats (wins, losses, streaks, likes, ratings, matches) |
| `/duels setrating <player> <-|kit> <amount>` | Set a rating (`-` = own-inventory) |
| `/duels resetrating <player> <-|kit|all>` (alias `resetr`) | Reset ratings |

## Lobby & misc

| Command | Description |
|---|---|
| `/duels setlobby` (alias `setspawn`) | Duel return lobby = your spot (player-only) |
| `/duels setkitlobby` | Kit-editor lobby = your spot (player-only) |
| `/duels lobby` | Teleport to the lobby (player-only) |
| `/duels spectate [player]` | Spectate (player permission `duels.spectate`, not admin) |
| `/duels playsound <name>` | Preview a configured `sounds.*` entry (player-only) |
| `/duels reload` (alias `rl`) | Reload configs |
| `/duels about` | Plugin info |
| `/duels help [category]` (alias `h`) | Categorized help |
