# Data, Saves & Backups

## Where player data lives

`plugins/AdvancedDuels/users/<uuid>.json` — one file per player: wins, losses, killstreaks, likes/dislikes, per-kit ratings, recent matches and rating history. Never hand-edit while the server runs.

## When it saves

| Trigger | What happens |
|---|---|
| Player quits | Async save (fire-and-forget) |
| Every `data.autosave-minutes` (default 10) | Async save of everyone cached (crash protection; `0` disables) |
| Plugin/server shutdown | **Synchronous flush of everything cached** — shutdowns and restarts never lose stats |

!!! tip "Panels that kill the process"
    A hard kill (`kill -9`, panel "kill") can only lose progress since the last autosave (≤10 min by default). Clean stops lose nothing.

## Memory cache

Online players plus recent quitters stay cached for speed. Players offline longer than `data.cache-minutes` (default 30, `0` disables) are saved and dropped from memory, then reloaded transparently on next access — `/duel stats <offline>`, likes and tops keep working. Name lookups always resolve.

## Config backups & migration

Before any `config.yml` / `commands.yml` / language migration, the current file is copied to `backups/` (e.g. `config-v22-2026-09-26_15-34-43-735.yml`). Migration only **adds** missing keys — your values and custom keys always win. If migration fails, your file is left untouched and the plugin runs with it as-is.

## Files you should back up externally

`arenas.json`, `kits.json`, `queues.json`, `signs.json`, `lobby.json`, `users/` — these are never touched by updates, but they're also never auto-backed-up. Include them in your regular server backups.
