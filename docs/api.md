# Developer API

Advanced Duels exposes a Java API (`ad.advancedDuels.api.*`) for extensions and integrations.

## Getting the API

```java
Duels duels = AdvancedDuels.getInstance(); // plugin instance also implements Duels
duels.getVersion();                        // e.g. "5.0"
```

Core entry points: `Duels` (scheduler helpers `doSync`/`doAsync*`, `registerSubCommand`, `registerListener`, `reload`, `teleportToLobby`) plus managers: `ArenaManager`, `KitManager`, `DQueueManager` (+ signs), `UserManager`, `SpectateManager`, `Request`.

## Events

Listen with a normal Bukkit listener:

| Event | Fired when |
|---|---|
| `MatchStartEvent` / `MatchEndEvent` | Match begins/ends (`MatchEndEvent.Reason`: tie, defeat, time, disable...) |
| `RequestSendEvent` / `RequestAcceptEvent` / `RequestDenyEvent` | Duel request lifecycle (cancellable) |
| `SpectateStartEvent` / `SpectateEndEvent` | Spectating begins/ends (start cancellable) |
| `ArenaCreateEvent` / `ArenaRemoveEvent` / `ArenaSetPositionEvent` / `ArenaStateChangeEvent` | Arena lifecycle |
| `KitCreateEvent` / `KitEquipEvent` / `KitRemoveEvent` | Kit lifecycle |
| `QueueCreateEvent` / `QueueRemoveEvent` / `QueueJoinEvent` / `QueueLeaveEvent` | Queue lifecycle |
| `QueueSignCreateEvent` / `QueueSignRemoveEvent` | Queue signs |
| `UserCreateEvent` | First-time userdata creation |

## Custom subcommands

```java
duels.registerSubCommand("duel", mySubCommand); // implements api.command.SubCommand
```

Names from `commands.yml` are resolved too (`commandKeyMap`), and duplicates are rejected with a console warning.

## Extensions

Extend `api.extension.DuelsExtension` and implement `onEnable()` / `onDisable()` for first-class extensions loaded from the plugin's `extensions/` folder via its own classloader.

## Users, matches, spectators

- `UserManager`: `getTopWins/Losses/Ratings`, per-user `User` (wins, losses, killstreaks, likes, ratings, matches).
- `Match`: bet, kit, players, items, duration, source queue.
- `SpectateManager.Result`: `SUCCESS, ALREADY_SPECTATING, IN_QUEUE, IN_MATCH, TARGET_NOT_IN_MATCH, DISABLED, EVENT_CANCELLED`.

!!! note "Scheduler"
    Always schedule through `Duels.doSync*/doAsync*` (Folia-aware) instead of Bukkit's scheduler directly — the plugin supports Folia.
