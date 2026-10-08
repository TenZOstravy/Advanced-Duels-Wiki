# `config.yml` Reference

Complete reference for every option (current `config-version: 25`). New keys merge in automatically on update — your values are never overwritten (see [Configuration Overview](index.md)).

## General

| Option | Default | Description |
|---|---|---|
| `lang` | `lang_EN` | Message file from `langs/`: `lang_EN`, `lang_DE`, `lang_ES`, `lang_FR`, `lang_PL`, `lang_RU`, `lang_CZ` |
| `check-for-updates` | `true` | Master switch for the update checker. `false` disables all update network traffic |
| `update-checker.source` | `NONE` | Update source. `NONE` = no checking. `CUSTOM` + `url` reads the latest version as plain text from your URL |
| `update-checker.url` | `''` | URL returning the latest version (only for `CUSTOM`) |
| `update-checker.download-url` | discord link | Shown in the update notification |
| `update-checker.notify-in-game` | `true` | Also notify players with `duels.update.notify` on join |

## `supported-plugins.*`

Only active when the plugin is installed **and** the hook message appears on console.

| Option | Default | Description |
|---|---|---|
| `CombatTagPlus/PvPManager/CombatLogX/DeluxeCombat.prevent-duel-if-tagged` | `true` | Tagged players cannot start duels |
| `...prevent-tag-in-duel` | `true` | No combat tag is applied inside duels |
| `Essentials.auto-unvanish` | `true` | Vanished players are unvanished when a duel starts |
| `Essentials.set-back-location` | `true` | Prevents `/back` from returning players into the arena — where they return is set by `duel.teleport-to-last-location` below |
| `mcMMO.disable-skills-in-duel` | `true` | mcMMO skills/abilities blocked in duels |
| `FactionsUUID` / `Factions.no-power-loss-in-duel` | `true` | No faction power loss on duel death |
| `WorldGuard.duelzone.enabled` / `.regions` | `false` / `[spawn, lobby]` | If enabled, duels can only start inside the listed regions |
| `MyPet.despawn-pet-in-duel` | `false` | Despawn pets on duel start |
| `BountyHunters` / `NotBounties.prevent-bounty-loss-in-duel` | `true` | Keep bounty on duel death |
| `SimpleClans.prevent-kdr-change` | `true` | Duel kills don't affect clan KDR |
| `LeaderHeads.wins/losses.menu.title` + `open-command` | `Duel Wins` / `openwins` … | LeaderHeads board integration |

## `request.*` — duel requests

| Option | Default | Description |
|---|---|---|
| `requires-cleared-inventory` | `false` | Players need an empty inventory to send/accept requests |
| `prevent-creative-mode` | `false` | Creative-mode players cannot duel |
| `use-own-inventory.enabled` | `true` | Allow fighting with your own gear instead of a kit. If `false`, the kit selector opens first |
| `use-own-inventory.drop-inventory-items` | `false` | **Dangerous:** drops own inventory on death and does NOT restore it. Increase `teleport-delay` so the winner can loot |
| `use-own-inventory.use-permission` | `false` | Gate own-inventory behind `duels.use.own-inventory` |
| `kit-selecting.enabled` / `.use-permission` | `true` / `false` | Kit picker in the request GUI (`duels.use.kit-select`) |
| `arena-selecting.enabled` / `.use-permission` | `true` / `false` | Arena picker in the request GUI (`duels.use.arena-select`) |
| `item-betting.enabled` / `.use-permission` | `true` / `false` | Item betting toggle in the request GUI (`duels.use.item-betting`) |
| `item-betting.allowed-worlds` | `[]` | Worlds where item betting is allowed (empty = everywhere). Anti-dupe boundary for cross-world item moves |
| `money-betting.enabled` / `.use-permission` | `true` / `false` | Money bets via `/duel <player> <amount>` (`duels.use.money-betting`, needs Vault) |
| `expiration` | `30` | Request expiry in seconds |

## `duel.match.*`

| Option | Default | Description |
|---|---|---|
| `max-duration` | `3` | Match time limit in minutes; `-1` disables |
| `boss-bar.enabled` | `true` | Show remaining-time boss bar in the last 2 minutes of timed matches |
| `boss-bar.color` | `RED` | `PINK, BLUE, RED, GREEN, YELLOW, PURPLE, WHITE` (invalid values fall back to `RED`) |
| `boss-bar.style` | `SOLID` | `SOLID, SEGMENTED_6, SEGMENTED_10, SEGMENTED_12, SEGMENTED_20` |
| `boss-bar.title` | `Time remaining: %time%` | `%time%` = `m:ss` |
| `rematch.enabled` | `true` | Clickable rematch offer to winner + loser after 1v1 duels |
| `rematch.expire-after` | `300` | Offer expiry in seconds (min 10) |
| `start-commands` | disabled | Console commands per player on match start (`%player%`, `{delay:ms}`) |
| `end-commands` | disabled | Console commands on match end (`%winner%`, `%loser%`, `%kit%`, `%arena%`, `%bet_amount%`, `{delay:ms}`) |
| `win-commands` | disabled | Same as above but only for the winner |
| `lose-commands` | disabled | Same as above but only for the loser |
| `*.queue-matches-only` | `false` | Restrict each command group to queue-started matches |

## `duel.*` — during & after the fight

| Option | Default | Description |
|---|---|---|
| `projectile-hit-message.enabled` / `.types` | `true` / arrows+trident | Tell shooters their victim's health on hit |
| `prevent-inventory-open` | `true` | Block all non-player inventories in duels |
| `protect-kit-items` | `true` | NBT-tag kit items so they can't be used outside duels |
| `remove-empty-bottle` | `true` | Delete empty bottles on potion drink (in duel) |
| `prevent-teleport-to-match-players` | `true` | Blocks `/tpa`-style teleports to duelists (bypass: `duels.teleport.bypass`) |
| `force-allow-combat` | `true` | Lets same-faction/team/party members damage each other in duels |
| `cancel-if-moved` | `false` | Cancel the duel if a player moves from the request spot |
| `forfeit.enabled` | `true` | Allow `/duel forfeit` (counts as a loss) |
| `enabled-worlds` | `[]` | Worlds where dueling works; empty = everywhere (list or `"A, B"` string) |
| `blacklisted-worlds` | `['world_name_here']` | Worlds where dueling is blocked |
| `send-death-messages` | `true` | Death messages to match players + spectators |
| `elimination-feed` | `true` | Elimination feed in team matches |
| `cooldown` | `0` | Seconds before a player may duel again (0 = off) |
| `teleport-to-last-location` | `false` | Return winners to their pre-duel spot instead of the lobby |
| `teleport-delay` | `5` | Seconds before the winner is teleported out |
| `spawn-firework` | `true` | Celebration firework at the death spot (`firework.color/type`) |
| `arena-only-end-message` | `false` | End message only to fighters + spectators instead of server-wide |
| `display-inventories` | `true` | Clickable end-of-match inventory preview (`/duel inventory <uuid>`) |
| `prevent-item-drop` / `clear-items-after-duel` | `false` / `true` | Block drops, or collect dropped items for cleanup after the match |
| `prevent-item-pickup` | `false` | Block ground pickups in duels |
| `limit-teleportation.enabled` / `.distance-allowed` | `true` / `5.0` | Max teleport distance in duels (ender pearls exempt; `-1` blocks all) |
| `block-all-commands` | `false` | If `true`, only `whitelisted-commands` work in duels; otherwise everything except `blacklisted-commands` works |

## `data.*` and `likes.*`

| Option | Default | Description |
|---|---|---|
| `data.autosave-minutes` | `10` | Periodic userdata saves (crash protection). `0` disables (quit/shutdown saves still run) |
| `data.cache-minutes` | `30` | Drop offline players from memory after N minutes (reloaded transparently). `0` disables |
| `likes.enabled` | `true` | `/duel like` / `/duel dislike` rating of recent opponents |
| `likes.window-minutes` | `30` | How long after a match opponents may rate each other (one rating per match) |

## `queue.*`, `rating.*`

| Option | Default | Description |
|---|---|---|
| `queue.blacklisted-commands` | `[]` | Commands blocked while queued |
| `rating.enabled` | `true` | ELO rating changes after matches |
| `rating.k-factor` | `32` | How strongly one match moves ratings |
| `rating.max-difference` | `400` | Max rating gap when queue-matching players |
| `rating.default-rating` | `1400` | Starting rating per kit |
| `rating.queue-matches-only` | `false` | Only queue matches change ratings |

## `spectate.*`

| Option | Default | Description |
|---|---|---|
| `enabled` | `true` | Master switch — `false` disables all spectating with a message |
| `wall-limit.enabled` / `.radius` | `true` / `25.0` | Leash spectators to the arena area; crossing it teleports them back |
| `requires-cleared-inventory` | `false` | Empty inventory required to spectate |
| `use-spectator-gamemode` | `false` | Use vanilla spectator mode instead of adventure+flight |
| `add-invisibility-effect` | `true` | Invisibility for spectators (ignored with spectator gamemode) |
| `whitelisted-commands` | msg-like list | Commands allowed while spectating |

## `countdown.*`, `party.*`

| Option | Default | Description |
|---|---|---|
| `countdown.enabled` | `true` | Pre-match countdown (length = message list) |
| `countdown.prevent.movement` / `.launch-projectile` / `.pvp` / `.interact` | all `true` | What's frozen during countdown |
| `countdown.duel.messages` / `.titles` | 5…1 + GO | Countdown texts and big titles (same list size required) |
| `countdown.party-duel.*` | same | Same for party duels (`%opponents%` supported) |
| `party.invite-expiration` | `30` | Party invite expiry (seconds) |
| `party.auto-disband-after` | `10` | Disband when owner offline N minutes (`-1` disables) |
| `party.max-size` | `10` | Max party members |
| `party.same-size-only` | `true` | Only equal-sized parties may duel |

## `stats.*`, `top.*`

| Option | Default | Description |
|---|---|---|
| `stats.display-kit-ratings` / `.display-nokit-rating` / `.display-past-matches` | `true` / `false` / `true` | Sections of `/duel stats` |
| `stats.matches-to-display` | `5` | Stored/shown past matches per player |
| `top.update-interval` | `5` | Leaderboard refresh (minutes) |
| `top.displayed-replacers.*` | wins/losses/killstreak/kit/no-kit | Titles + identifiers for `/duel top` categories |

## `guis.*`, `soup.*`, `sounds.*`, misc

| Option | Default | Description |
|---|---|---|
| `guis.settings.rows`, `.details-button.slot`, `.option-button-slots`, `.send-button.*`, `.cancel-button.*`, `.*-button.item` | see file | Layout and materials of the duel request GUI |
| `guis.kit-selector.rows`, `.arena-selector.rows`, `.queues.rows`, `.space-filler-item`, `.inherit-kit-item-type` | 2 / 3 / 2 | Paged selector GUIs |
| `soup.hearts-to-regen` / `.remove-empty-bowl` / `.cancel-if-already-full` | `3.5` / `true` / `true` | Mushroom-soup healing in SOUP kits |
| `sounds.*` | piano/pling | Sounds bound to countdown messages (1.8 vs 1.9+ variants) |
| `firework.color` / `.type` | `AQUA` / `BALL_LARGE` | End-of-match firework style |
| `disable-enderpearl-in-endgame` | `true` | No pearls during the endgame window |
| `disable-movement-in-endgame` | `false` | Freeze movement during the endgame window |
| `user-not-found`, `not-in-match`, `duration-format`, `no-kit`, `no-opponent` | — | PlaceholderAPI fallback texts |
| `use-minimessages` | `false` | Parse messages as MiniMessage instead of `&` codes |
| `arena-regen.block-tracking-enabled` | `false` | Record and restore arena block changes (see [Regeneration](../arenas/regeneration.md)) |
