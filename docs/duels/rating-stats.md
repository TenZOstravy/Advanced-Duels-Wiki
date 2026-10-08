# Rating, Stats, Killstreaks & Likes

## ELO rating

Each kit (plus own-inventory mode) has its own rating, starting at `rating.default-rating` (1400). Wins move points from loser to winner scaled by `rating.k-factor` (32).

```text
/duel stats [player]     # your stats, ratings, killstreak, likes, past matches
/duel top [wins|losses|killstreak|kit|-]
```

- `rating.queue-matches-only: true` limits rating changes to queue matches.
- Queue matchmaking pairs players within `rating.max-difference` (400).
- Admins: `/duels setrating <player> <-|kit> <amount>`, `/duels resetrating <player> <-|kit|all>`.

## Leaderboards

`/duel top` categories: `-` (own-inventory rating), `wins`, `losses`, `killstreak`, or a kit name for its rating board. Boards refresh every `top.update-interval` minutes (default 5); titles come from `top.displayed-replacers.*`.

## Killstreaks

Kills in duels raise your streak; dying (or forfeiting) resets it. Best streak is kept forever. Shown in `/duel stats`, ranked in `/duel top killstreak`, and available as `%duels_killstreak%` / `%duels_best_killstreak%` placeholders.

## Likes & dislikes

After a match, opponents can rate each other:

```text
/duel like <player>
/duel dislike <player>
```

Rules (`likes.*`): only opponents from a match that ended within `window-minutes` (default 30), one rating per player per match, no self-rating, toggleable via `likes.enabled`. Totals show in `/duel stats` (`%duels_likes%`, `%duels_dislikes%`). Designed as a lightweight sportsmanship signal.

## Rematch

After 1v1 duels both sides get a clickable **[REMATCH]** that re-sends the same settings (kit, arena, bets re-validated). Offers expire after `duel.match.rematch.expire-after` (300 s), or type `/duel rematch [player]` manually. No offers for party, forced or tied matches.
