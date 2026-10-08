# Arena Regeneration

Regeneration restores blocks that were broken, placed or exploded inside an arena while a duel was running — so the next match starts on a pristine map. No WorldEdit needed: the plugin records changes with Bukkit events and rolls them back when the match ends.

## How it works

1. Before a match, tracking starts for that arena **if** it has bounds set **and** block tracking is enabled.
2. Every block break/place/explosion inside the bounds is recorded (original state only — lightweight).
3. When the match ends, recorded blocks are restored.

!!! warning "Bounds are required"
    If an arena has no bounds, tracking is skipped with a console warning telling you to run `/duels arenaregen enable <arena>`. Setting `block-tracking-enabled: true` alone is not enough.

## Setup

```text
# 1. Enable tracking globally
arena-regen.block-tracking-enabled: true     # in config.yml, then restart or /duels reload

# 2. In game: get the selection wand
/duels wand

# 3. Select two corners (left/right click), then bind them to the arena
/duels arenaregen enable <arena>
```

Useful extras:

| Command | What it does |
|---|---|
| `/duels arenaregen status [arena]` | Show whether bounds exist and tracking state |
| `/duels arenaregen disable <arena>` | Remove an arena's bounds (tracking stops for it) |
| `/duels arenaregen onlyarena` | Scope the current selection to one arena (see usage text in game) |
| `/duels regen status` | Global regen system status |

Aliases: `aregen`, `regenbounds` for `arenaregen`; `tracker`, `blocktrack` for `regen`.

## Configuration

```yaml
arena-regen:
  block-tracking-enabled: false   # default: off
```

## Limitations

- Only changes **inside the bounds** are tracked — build bounds generously around the playable area.
- Only block break/place/explosion events are recorded (custom plugin shenanigans outside Bukkit events are not).
- Very block-heavy modes (TNT spam) record more data, but only original states — one entry per changed block.
