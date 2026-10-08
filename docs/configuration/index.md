# Configuration Overview

Advanced Duels stores its configuration in `plugins/AdvancedDuels/`. There is **no `messages.yml`** — messages live in the `langs/` folder instead.

## Files

| File | What it controls | Migrated on update? |
|---|---|---|
| `config.yml` | Everything gameplay-related (duels, betting, queues, rating, spectating, GUIs...) | Yes, with backup |
| `commands.yml` | Command names and aliases (`duel`, `party`, `queue`, `duels`, `kit`) | Yes, with backup |
| `langs/lang_XX.yml` | All chat messages, GUI texts and usages (7 languages included) | Yes — missing keys merged in |
| `arenas.json`, `kits.json`, `queues.json`, `signs.json` | Your arenas, kits, queues, signs (managed in-game, don't hand-edit) | Never touched |
| `users/*.json` | Per-player stats, ratings, likes, match history | Never touched |
| `lobby.json`, `kit_lobby.json` | Duel lobby positions | Never touched |
| `backups/` | Timestamped copies made before any migration | — |

## Safe updates

Updating never overwrites your settings:

1. On boot the plugin compares each file's `config-version` with the version shipped in the jar.
2. If yours is older, the current file is copied to `backups/` (e.g. `backups/config-v22-2026-09-26_15-34-43-735.yml`).
3. New default keys are **added**; your existing values always win; unknown/custom keys are preserved.
4. If a file is already current but still misses keys (e.g. after a manual edit), the missing keys are healed the same way.

If migration ever fails, the original file is left untouched and the plugin continues with it — it never replaces your config with defaults. Details: [Data & Backups](../data.md).

!!! tip "Reloading config"
    `/duels reload` reloads configuration without a restart. Prefer a full restart after updating the **jar itself**.

## Where things live

- Gameplay tuning → [`config.yml` reference](config-reference.md)
- Renaming `/duel` etc. → `commands.yml` (`commands.<name>.name` + `aliases`, all lowercased automatically)
- Any text players see → [`langs/` language files](languages.md)
- PlaceholderAPI fallback texts (`user-not-found`, `not-in-match`, ...) → bottom of `config.yml`

## MiniMessage or legacy colors?

`use-minimessages: false` by default — messages use classic `&` color codes. Set it to `true` to parse messages as MiniMessage instead (e.g. `<red>text</red>`, gradients). There is also a `lang_minimessages.yml` resource with MiniMessage-styled defaults for reference.
