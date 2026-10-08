# Requests: Accept, Deny, Expiry

## How requests work

1. The challenger configures the duel (GUI or command args) and sends the request.
2. The target gets a message with clickable **[ACCEPT]** / **[DENY]**.
3. On accept with item betting enabled, **both** players place items into the shared betting GUI and confirm — only then does the match start.
4. Otherwise the match starts immediately (after the countdown, if enabled).

```text
/duel accept <player>
/duel deny <player>
```

Requests expire after `request.expiration` seconds (default 30). Accepting in a disallowed world is rejected.

## Opting out

`/duel toggle` flips whether you accept duel requests (`duels.toggle`, default: on for everyone). Party invites have their own toggle: `/party toggle` (`duels.party.toggle`).

## For admins

- `/duels edit <player> <add|remove|set> <wins|losses> <amount>` — correct a player's record.
- `/duels reset <player>` — wipe a player's full stats (wins, losses, streaks, likes, ratings, matches).
- `/duels resetrating <player> <-|kit|all>` — reset ratings only.
- `/duels setrating <player> <-|kit> <amount>` — set a rating directly.
