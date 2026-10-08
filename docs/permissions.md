# Permissions

`duels.*` grants everything. Unlisted permissions default to OP-only. Everyone gets `duels.default` automatically.

## Default kit (`duels.default` — all players)

| Permission | Allows |
|---|---|
| `duels.duel` | `/duel` challenges, accept/deny, lobby, queue-toggle, spectate browser, rematch, like/dislike, forfeit, inventory view, version |
| `duels.stats` | `/duel stats` (own) |
| `duels.toggle` | `/duel toggle` |
| `duels.top` | `/duel top` |
| `duels.spectate` | Spectating (`/duel spectate`, `/duels spectate`) |

## Admin (`duels.admin` — also grants the tree below)

Full `/duels` access (except `/duels spectate`, which uses `duels.spectate`), plus:

| Permission | Allows |
|---|---|
| `duels.update.notify` | Update notifications on join |
| `duels.teleport.bypass` | Teleport to duelists despite `prevent-teleport-to-match-players` |
| `duels.force` | `--force` duels, bypass enabled-world restriction (default: OP) |
| `duels.spectate.anonymously` | Spectate without join/leave announcements |
| `duels.kits.*` | All kits |
| `duels.use.*` | All request-setting options |
| `duels.queue` | Named queues |
| `duels.stats.others` | `/duel stats <player>` |
| `duels.party` / `duels.party.toggle` / `duels.party.list.others` | Party system bits |
| `duels.kiteditor` | `/kit edit`, `/kit save` |

## Granular request options

Only enforced when the matching `use-permission` is `true` in `config.yml`:

| Permission | Gates |
|---|---|
| `duels.use.kit-select` | Kit picker |
| `duels.use.own-inventory` | Own-inventory mode |
| `duels.use.arena-select` | Arena picker |
| `duels.use.item-betting` | Item betting |
| `duels.use.money-betting` | Money betting |
| `duels.kits.<kitname>` | A specific kit (spaces become `-`, lowercase) |

!!! tip "Hiding admin commands"
    Rename commands or change aliases in `commands.yml` if they collide with other plugins. All names are lowercased automatically.
