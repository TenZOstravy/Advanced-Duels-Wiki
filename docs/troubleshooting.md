# Troubleshooting

Each entry: **Problem → Likely cause → Fix**.

## "No arena available" when dueling
→ Arena missing, disabled, or without both positions. → `/duels list` (green = usable), then `create`/`set`/`toggle` as needed. Also check kit↔arena bindings (`/duels bind`) — a kit bound to zero usable arenas never starts.

## Requests instantly expire / accept does nothing
→ Cooldown active, player moved with `cancel-if-moved: true`, or acceptor in a disabled world. → Check `duel.cooldown`, stand still, accept in an enabled world.

## Winner goes to spawn instead of pre-duel spot
→ That's `duel.teleport-to-last-location: false` (lobby return). → Set it `true` for last-location returns. (Essentials `set-back-location` only controls `/back`, not the duel return itself.)

## `/back` leads into the arena
→ Essentials hook inactive. → Install Essentials and keep `supported-plugins.Essentials.set-back-location: true`; confirm the hook message on console.

## Kit items work outside duels
→ `duel.protect-kit-items` is `false`. → Enable it (tags stay attached even while toggled off, so re-enabling is safe).

## Teleporting (pearls, abilities) behaves oddly in duels
→ `duel.limit-teleportation` (ender pearls are always exempt). → Raise `distance-allowed` if players get stuck, or disable the limiter.

## Queue never pops
→ Rating gap above `rating.max-difference`, no free compatible arena, or bet mismatch. → Widen the gap, check arenas, align bets/kits.

## Signs don't update / can't be broken
→ Signs refresh on a timer; hand-breaking queue signs is blocked by design. → `/duels delsign` while looking at the sign.

## Spectator stuck / can't leave area
→ Wall limit (`spectate.wall-limit`) pulls leavers back — intended. → Run the spectate command again to stop, or disable/raise the limit.

## `Failed to load message` in console
→ A lang key or `%placeholder%` was renamed or deleted in `langs/`. → Restore the key from the jar defaults (compare with a fresh file); never rename keys.

## `Could not load userdata ...` on boot
→ A `users/<uuid>.json` is corrupt. → The file is skipped (not deleted). Restore it from your server backups, or delete it to start that player fresh.

## Update notice shows `null` download link
→ `update-checker.download-url` is empty. → Set it to your download page, or `check-for-updates: false` to silence checking.

## Lag during big fights
→ The plugin's hot paths are map lookups and guarded listeners; heavy cost usually comes from elsewhere (scoreboards polling placeholders are fine — they're O(1)). → Profile with Spark; common real causes are oversized arenas with block-tracking on TNT-heavy kits.
