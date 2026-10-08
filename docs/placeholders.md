# Placeholders

Requires [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/). Prefix: **`%duels_...%`**. Every lookup is a cheap map read — safe for scoreboards and tablists that poll constantly.

## Player stats

| Placeholder | Example output |
|---|---|
| `%duels_wins%` | `12` |
| `%duels_losses%` | `5` |
| `%duels_killstreak%` | `3` |
| `%duels_best_killstreak%` | `7` |
| `%duels_likes%` | `9` |
| `%duels_dislikes%` | `1` |
| `%duels_wl_ratio%` / `%duels_wlr%` | `2.4` |
| `%duels_average_rating%` / `%duels_avg_rating%` | `1452.50` |
| `%duels_rating_-%` | `1400` (own-inventory rating) |
| `%duels_rating_<kit>%` | e.g. `%duels_rating_Diamond%` |
| `%duels_can_request%` | `true` |
| `%duels_inmatch%` | `true` / `false` (fighting right now) |
| `%duels_arena%` | `Colosseum` (fighting/spectating arena) |

Unknown-data fallbacks come from the bottom of `config.yml` (`user-not-found`, `not-in-match`, `no-kit`, `no-opponent`).

## Queues

| Placeholder | Example output |
|---|---|
| `%duels_isinqueue_<queue>%` | `Yes` / `No` |
| `%duels_getplayersinqueue_<queue>%` | `3` |
| `%duels_getplayersplayinginqueue_<queue>%` | `2` |

`<queue>` is the queue name (kit+bet fallback parsing supported).

## Current match (fighter or spectator)

| Placeholder | Example output |
|---|---|
| `%duels_match_duration%` | `01:23` |
| `%duels_match_kit%` | `Diamond` |
| `%duels_match_arena%` | `Colosseum` |
| `%duels_match_bet%` | `100` |
| `%duels_match_rating%` | Your rating for this kit |
| `%duels_match_opponent%` | `Steve` |
| `%duels_match_opponent_health%` | `7.0` (hearts) |
| `%duels_match_opponent_ping%` | `42` |
| `%duels_match_opponent_rating%` | `1510` |
