# FAQ

## How do I create an arena?
`/duels create <name>` → `/duels set <name> 1` and `2` at the spawn spots → `/duels toggle <name>`. Verify with `/duels info <name>`. Full guide: [Arenas](arenas/index.md).

## How do I enable arena regeneration?
Set `arena-regen.block-tracking-enabled: true`, restart, take the `/duels wand`, select two corners and run `/duels arenaregen enable <arena>`. See [Regeneration](arenas/regeneration.md).

## How do I enable spectators?
Spectating is on by default (`spectate.enabled`). Players use `/duel spectate`. Tune the leash (`wall-limit`), gamemode and invisibility in `spectate.*`. See [Spectating](spectating.md).

## How do I change messages?
Edit `plugins/AdvancedDuels/langs/lang_<XX>.yml`. Never rename keys or `%placeholders%`. Switch files with `lang:` in `config.yml`. See [Languages](configuration/languages.md).

## How do I change duel settings?
Most gameplay tuning is `config.yml` ([reference](configuration/config-reference.md)). Request-GUI options (own inventory, kit/arena pickers, betting) have individual `enabled` + `use-permission` switches under `request.*`.

## Why isn't a command working?
1. Check the permission ([reference](permissions.md)) — most admin commands need `duels.admin`.
2. Check `commands.yml` — the command may be renamed on your server.
3. In a duel/queue/spectate? Command blacklists apply (`duel.blacklisted-commands`, `queue.blacklisted-commands`, spectate allowlist).
4. In a disabled world? Check `duel.enabled-worlds` / `blacklisted-worlds`.

## Why can't players duel?
Walk the checklist: free **enabled** arena with both positions? (`/duels list`, `/duels info`) Both players accepting requests (`/duel toggle`)? No cooldown, right world, cleared inventory if required, not in creative if blocked, not combat-tagged, request not expired (30 s)?

## Why is money betting rejected?
Needs Vault **plus** an economy provider, `request.money-betting.enabled: true`, and enough balance on both sides.

## What permissions do players need?
Nothing — `duels.default` (duel, stats, toggle, top, spectate) is granted to everyone. See [Permissions](permissions.md).

## Stats reset after restart — help!
This was a save-path bug fixed by the shutdown flush + autosave: make sure you're on the latest jar. Stats live in `users/*.json` and flush on quit, every `data.autosave-minutes`, and fully on shutdown. If files exist but show zeros, check startup errors (`Could not load userdata`) — a corrupt JSON is skipped, never deleted.

## My config didn't update!
The migrator only *adds* missing keys — it never rewrites your values. Check `config-version` at the top and `backups/` for what changed. If a file is current but lacks keys, they're healed on next boot automatically.
