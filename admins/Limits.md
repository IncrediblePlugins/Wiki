# Limits

BetterFarming uses `player-limits.yml` for permission-based and playtime-based limits.

If `packs.stack` is `false`, the first matching pack is used. If it is `true`, every matching pack is added together.

Set a limit to `-1` for unlimited. Limits that are missing from a pack are treated as `0`.

# BetterFarming Limit IDs

| Limit | What it controls |
| --- | --- |
| `player_farms_total` | Total farms a player can create, regardless of farm type. |
| `player_farms_<type>` | Farms of one type a player can create. The `<type>` part is the farm type key from `farms.yml`, such as `player_farms_crop` or `player_farms_tree`. |
| `farm_members` | Trusted players per farm. |
| `player_groups` | Reserved by the trusted-player framework. BetterFarming's default farm UI does not normally use player-created groups. |

Farm-type limits are registered automatically from the enabled type keys in `farms.yml`.

# Example

```yaml
packs:
  stack: false
  vip:
    permission: "betterfarming.limits.vip"
    limits:
      player_farms_total: 25
      player_farms_crop: 15
      player_farms_tree: 10
      farm_members: 20

  default:
    limits:
      player_farms_total: 10
      player_farms_crop: -1
      player_farms_tree: -1
      farm_members: 10
```

# Playtime Rewards

The `time-rewards` section can add limits after players spend time on the server.

For example, a reward on `player_farms_total` can grant players another farm slot every configured period until the configured maximum is reached.

# Admin Limit Commands

| Command | What it does |
| --- | --- |
| `/farm admin player <player> limits` | Shows a player's effective limits, split into configured pack, command-given modifier, and playtime reward values. |
| `/farm admin player <player> give limit <limit> <amount>` | Adds or removes a command-given modifier for an online player. Use a negative amount to remove from the command-given modifier. |

Command-given removals cannot remove limits that come from `player-limits.yml` packs or playtime rewards.
