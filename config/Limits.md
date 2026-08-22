# Limits

Player limits are configured in `player-limits.yml`.

Limits can be assigned through limit packs, permissions, playtime rewards, and admin commands.

# Limit IDs

| Limit ID | Permission prefix | What it controls |
| --- | --- | --- |
| `player_blocks` | `chestprotect.blocks` | Maximum block protections. |
| `player_blocks_free` | `chestprotect.free.blocks` | Free block protections before costs apply. |
| `player_entities` | `chestprotect.entities` | Maximum entity protections. |
| `player_entities_free` | `chestprotect.free.blocks` | Free entity protections before costs apply in the current plugin build. |
| `player_groups` | `chestprotect.groups` | Maximum groups a player can create. |
| `protection_members` | `chestprotect.members` | Maximum trusted players per protection or group. |

Use the IDs in `player-limits.yml`, admin limit commands, PlaceholderAPI placeholders, and API
calls.

# Limit Packs

Limit packs are configured under `packs`.

The first pack whose permission the player has is assigned when the player joins. If no permission
is configured for a pack, it can act as the default pack.

Example:

```yaml
packs:
  default:
    limits:
      player_blocks: 40
      player_blocks_free: 0
      player_entities: 20
      player_entities_free: 0
      player_groups: 10
      protection_members: 10
```

Use `-1` for no limit. Limits omitted from a pack are treated as `0`.

# Numbered Permissions

You can also assign numbered permissions:

| Permission | What it sets |
| --- | --- |
| `chestprotect.blocks.<number>` | Block protection limit. |
| `chestprotect.entities.<number>` | Entity protection limit. |
| `chestprotect.groups.<number>` | Group limit. |
| `chestprotect.members.<number>` | Trusted members per protection or group. |
| `chestprotect.free.blocks.<number>` | Free block protections, and currently free entity protections in the plugin build. |

If `general.permission-stacking` is `true`, multiple numbered permissions are added together.
Otherwise, the highest matching value is used.

# Playtime Rewards

`time-rewards` can add limits based on player playtime. Time units are `s`, `m`, `h`, and `d`.

Example:

```yaml
time-rewards:
  player_blocks:
    time: 1h
    max: 100
```

This gives one additional block protection per hour until the player reaches the configured reward
maximum.

# Admin Limit Commands

Use `/chestprotect admin player <player> give limit <limit> <amount>` for manual adjustments.

For normal rank-based setups, prefer limit packs and numbered permissions.
