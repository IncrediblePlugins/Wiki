# Levels

Spawner upgrade levels are configured in `levels.yml`.

UpgradeableSpawners uses separate level tracks. It does not use one combined "spawner level."

# Level Tracks

| Section | Player-facing upgrade | Notes |
| --- | --- | --- |
| `spawn_interval` | Spawn Interval | Lower values are better. Values in `levels.yml` are written in seconds. |
| `spawn_amount` | Spawn Amount | How many entities the spawner tries to spawn each time. |
| `period_amount` | Spawns During Period | How many entities the spawner may spawn during the configured period. |
| `player_range` | Player Distance | How close a player must be for the spawner to run. Higher values are better. |
| `nearby_entities` | Nearby Entities | How many nearby entities of the same type are allowed before pausing. |

# Level Format

Each level has a numeric id, a value, and a cost.

```yaml
spawn_interval:
  1:
    value: 60
    cost: 0
  2:
    value: 55
    cost: 1000.0
```

The numeric id is the level id used by admin commands such as `/spawners admin give`.

# Required Level 1

Every level track should have level `1`. New spawners start at the configured entry level for each
track.

# Disabling an Upgrade

If you do not want players to use an upgrade, hide or disable the related item in the GUI menu and
keep a valid level in `levels.yml`.

Do not remove a whole level track unless you know the plugin version supports that setup.

# Period Amount

The period length is configured in `config.yml` under the period limit settings.

If the period is disabled, the Spawns During Period upgrade no longer limits spawning.
