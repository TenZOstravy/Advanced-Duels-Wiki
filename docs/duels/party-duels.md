# Party Duels

Parties let groups fight as teams. Only equally-sized parties can duel each other by default (`party.same-size-only: true`).

## Party basics

| Command | What it does |
|---|---|
| `/party <player>` | Invite a player (creates the party, you become owner) |
| `/party accept <player>` | Accept an invite |
| `/party leave` | Leave (owner must transfer first or disband) |
| `/party kick <player>` | Owner kicks a member |
| `/party transfer <player>` | Pass ownership |
| `/party disband` | Owner disbands |
| `/party list` | Show members |
| `/party toggle` | Block party invites |
| `/party friendlyfire` | Allow party members to hit each other (alias `ff`) |

Relevant permissions: `duels.party`, `duels.party.toggle`, `duels.party.list.others`.

## Starting a party duel

Challenge while in a party: `/duel <player>` (target's party is picked up automatically). The party leaders get the accept flow; on accept the whole teams are teleported in.

Limitations:

- No money or item betting in party duels.
- All members share kit/arena choice from the request.

## During the match

Dead teammates stay in the arena as spectators. Elimination messages show if `duel.elimination-feed` is on. When one team is wiped, ratings/wins resolve per team and everyone is teleported out after `teleport-delay`.

## Configuration

```yaml
party:
  invite-expiration: 30     # invite expiry (seconds)
  auto-disband-after: 10    # disband when owner offline N minutes (-1 = never)
  max-size: 10
  same-size-only: true
```
