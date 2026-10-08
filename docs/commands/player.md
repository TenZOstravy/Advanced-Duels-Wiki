# Player Commands

All commands and aliases can be renamed in `commands.yml`. Default permissions: everyone gets `duel`, `stats`, `toggle`, `top` and `spectate` (via `duels.default`); everything else needs OP or an explicit grant.

## `/duel`

Base permission: `duels.duel` (everyone). All subcommands are player-only.

| Command | Description |
|---|---|
| `/duel <player>` | Open the request settings GUI for a duel |
| `/duel <player> <bet> [true] [kit\|-]` | Send a configured request immediately (bet = Vault money, `true` = item betting, kit name or `-` for own inventory) |
| `/duel <player> ... --force` | Start immediately without accept (needs `duels.force`; no item betting) |
| `/duel accept <player>` | Accept a request (opens item-bet GUI if enabled) |
| `/duel deny <player>` | Decline a request |
| `/duel stats [player]` | Stats, ratings, killstreak, likes, past matches (others need `duels.stats.others`) |
| `/duel top [-|wins|losses|killstreak|kit]` | Leaderboards (`-` = own-inventory rating). Needs `duels.top` |
| `/duel toggle` | Stop/allow receiving duel requests. Needs `duels.toggle` |
| `/duel lobby` | Teleport to the duel lobby |
| `/duel queue` | Toggle the quick-match simple queue |
| `/duel spectate [player]` | Open the live-match browser, or spectate directly. Needs `duels.spectate` |
| `/duel rematch [player]` | Re-send the last match's settings (1v1 offers, 5-min expiry) |
| `/duel like <player>` / `/duel dislike <player>` | Rate a recent opponent (30-min window, one per match) |
| `/duel forfeit` | Leave the current match as a loss |
| `/duel _ <uuid>` | Open a post-match inventory preview (used via clickable chat message, not typed) |
| `/duel version` (alias `v`) | Plugin version |

Requests expire after `request.expiration` seconds and are validated on accept (world, cooldown, inventory, cooldown, combat-tag...).

## `/party` (alias `p`, `duelparty`, `dp`)

Base permission: `duels.party`. Bare `/party <player>` sends an invite.

| Command | Permission | Description |
|---|---|---|
| `/party <player>` | `duels.party` | Invite (creates the party, you own it) |
| `/party accept <player>` (alias `a`) | `duels.party` | Accept an invite |
| `/party leave` (alias `l`) | `duels.party` | Leave (owner must transfer/disband instead) |
| `/party kick <player>` (alias `remove`) | `duels.party` | Owner kicks a member |
| `/party transfer <player>` | `duels.party` | Pass ownership |
| `/party disband` | `duels.party` | Owner disbands |
| `/party list` (alias `ls`) | `duels.party` | List members |
| `/party toggle` | `duels.party.toggle` | Block party invites |
| `/party friendlyfire` (alias `ff`) | `duels.party` | Allow hitting party members |

## `/queue` (alias `q`)

Base permission: `duels.queue`.

| Command | Description |
|---|---|
| `/queue` | Open the queue browser GUI |
| `/queue join <name>` (alias `j`) | Join a queue (money bet taken on join) |
| `/queue leave` (alias `l`) | Leave the queue |

## `/kit`

| Command | Permission | Description |
|---|---|---|
| `/kit edit <kit>` | `duels.kiteditor` | Visual kit editor (save with `/kit save`) |
| `/kit save` | `duels.kiteditor` | Save + exit the editor |

## `/duels spectate [player]`

Needs `duels.spectate` (NOT `duels.admin` — the subcommand carries its own permission). Same behavior as `/duel spectate`: browser GUI without args, direct spectate with a name, toggle-off when already spectating.
