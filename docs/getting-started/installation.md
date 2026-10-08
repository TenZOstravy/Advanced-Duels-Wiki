# Installation

## Requirements

| Requirement | Details |
|---|---|
| Server software | Spigot or Paper, Minecraft 1.21.x recommended (Folia is supported) |
| Java | Java 21 |
| Disk space | A few MB for configs, kits, arenas and per-player data files |

!!! note "Paper recommended"
    Advanced Duels runs on both Spigot and Paper, but Paper (or a Paper fork) is recommended for performance and Folia compatibility.

## Optional dependencies

These plugins unlock extra features when installed. Everything is a **soft dependency** — the plugin works fine without them.

| Plugin | Unlocks |
|---|---|
| Vault + economy plugin | Money betting (`/duel <player> <amount>`) |
| PlaceholderAPI | All `%duels_*` placeholders (see [Placeholders](../placeholders.md)) |
| Essentials | Anti-vanish on duel start, `/back` protection in arenas |
| WorldGuard | Duel-only regions (`duelzone`) |
| CombatTagPlus / PvPManager / CombatLogX / DeluxeCombat | Block duels while combat-tagged, no tagging inside duels |
| mcMMO | Disable skills inside duels |
| MyPet | Despawn pets on duel start |
| Factions / FactionsUUID | No power loss on duel death |
| SimpleClans | Keep KDR unchanged by duels |
| BountyHunters / NotBounties | No bounty loss on duel death |
| LeaderHeads / MVdWPlaceholderAPI | Leaderboard integrations |
| Multiverse-Core / MyWorlds / MultiWorld | Better loading order for arenas in managed worlds |
| AxGraves | Grave handling in duels |

See [Integrations](../integrations.md) for per-plugin settings.

## Installing

1. Download `AdvancedDuels.jar`.
2. Place it in your server's `plugins/` directory.
3. Restart the server (a full restart, not `/reload` — especially when updating).
4. Check the console for `Successfully enabled AdvancedDuels`. If you see hook messages like `Successfully hooked into 'Vault'!`, those integrations are active.

## Files created

On first start the plugin creates (inside `plugins/AdvancedDuels/`):

| File / folder | Purpose |
|---|---|
| `config.yml` | Main configuration |
| `commands.yml` | Command names and aliases |
| `langs/` | Message files (`lang_EN.yml`, `lang_DE.yml`, …) |
| `users/` | One JSON file per player (stats, ratings, likes) |
| `arenas.json`, `kits.json`, `queues.json`, `signs.json` | Your arenas, kits, queues and signs |
| `lobby.json`, `kit_lobby.json` | Duel lobby positions |
| `backups/` | Automatic backups before every config migration |
| `logs/` | Plugin log files |

!!! warning "Updating? Don't use /reload"
    Always do a full server restart when updating the jar. Reloading can leave stale classes in memory. Your settings are safe: updates migrate `config.yml` automatically with a backup (see [Data & Backups](../data.md)).

## Next step

Continue with [First Setup](first-setup.md) — lobby, first arena and first kit in about five minutes.
