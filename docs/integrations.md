# Integrations

All integrations are optional soft-depends. A hook is active only when the plugin is installed **and** you see `Successfully hooked into '<name>'!` on console. Per-plugin toggles live under `supported-plugins.*` in `config.yml`.

## Economy & betting

**Vault** (+ any Vault economy): enables money betting (`/duel <player> <amount>`, queue bets). Without an economy provider, money bets are rejected — item betting still works.

## Anti-combat-log

**CombatTagPlus / PvPManager / CombatLogX / DeluxeCombat**: `prevent-duel-if-tagged` blocks dueling while tagged; `prevent-tag-in-duel` keeps duels tag-free.

## Essentials

- `auto-unvanish`: unvanish fighters on match start.
- `set-back-location`: stops `/back` from leading into the arena. (Where winners go is still `duel.teleport-to-last-location`.)

## Protection & clans

| Plugin | Effect |
|---|---|
| WorldGuard | `duelzone.enabled` + `regions`: duels only inside listed regions |
| Factions / FactionsUUID | No power loss on duel death |
| SimpleClans | Duel kills don't touch KDR |
| AxGraves | Grave handling inside duels |
| MyPet | `despawn-pet-in-duel` |
| mcMMO | `disable-skills-in-duel` |
| BountyHunters / NotBounties | No bounty loss in duels |
| LeaderHeads / MVdWPlaceholderAPI | Wins/losses leaderboard menus |

## Placeholders & worlds

- **PlaceholderAPI**: all `%duels_*` placeholders (see [Placeholders](placeholders.md)).
- **Multiverse-Core / MyWorlds / MultiWorld**: soft-depends so arenas load after world managers (fixes null locations when Duels loads first).

## Metrics & updates

- **bStats**: anonymous usage statistics (metrics ID in source). No configuration needed.
- **Update checker**: async, notify-only (never downloads). Configure `check-for-updates` + `update-checker.*`; in-game notices need `duels.update.notify`.
