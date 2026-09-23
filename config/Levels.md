# Levels

Spawner upgrade levels are configured in `spawners.yml`, under `types.spawner.levels`.

A spawner has **one combined level** — there are no separate upgrade tracks. Every level bundles
values for all five attributes below, plus one combined cost for that level.

This file is not hot-reloadable. Editing it requires a server restart, and editing/removing a
level while spawners are already placed can shift what an existing spawner's stored level number
now means — see the note at the bottom before editing an existing setup.

# Attributes

| Attribute key | Player-facing stat | Notes |
| --- | --- | --- |
| `spawn-interval` | Spawn Interval | Lower values are better. Written in **seconds** (converted to ticks internally). |
| `nearby-entities` | Nearby Entities | How many nearby entities of the same type are allowed before pausing. |
| `player-range` | Player Distance | How close a player must be for the spawner to run. Higher values are better. |
| `spawn-amount` | Spawn Amount | How many entities the spawner tries to spawn each time it runs. |
| `period-amount` | Spawns During Period | How many entities the spawner may spawn during the configured period. |

# Level Format

Each level under `types.spawner.levels` has a numeric id (levels are read in the order they
appear — the numeric id is just a label), a display name, a cost, and a value for every attribute:

```yaml
types:
  spawner:
    levels:
      1:
        name: "I"
        cost: 0
        attributes:
          spawn-interval: { value: 60 }
          nearby-entities: { value: 8 }
          player-range: { value: 16 }
          spawn-amount: { value: 3 }
          period-amount: { value: 30 }
      2:
        name: "II"
        cost: 1000
        attributes:
          spawn-interval: { value: 55 }
          nearby-entities: { value: 12 }
          player-range: { value: 25 }
          spawn-amount: { value: 3 }
          period-amount: { value: 50 }
```

Every attribute's value is the **literal** number a spawner at that level uses — not a percentage
or a bonus on top of a base value. You can add as many levels as you want; the numeric id used by
`/spawners admin give ... [level]` is the level number as it appears in this file.

# Stacking Options

The `stacking` section under a spawner type controls stacking specifically for that type. General
stacking behavior (merge radius, sneak-break behavior, drop format, ...) lives in `config.yml` —
see [Configuration](Configuration.md#spawner-stacking).

```yaml
types:
  spawner:
    stacking:
      max: 64
      scale-attributes:
        - spawn-amount
        - nearby-entities
        - period-amount
```

| Option | Use |
| --- | --- |
| `stacking.max` | Maximum stack size for this type. The lower of this and `config.yml`'s `stacking.max-stack` applies. Set to `1` to stop this type from being stacked at all. |
| `stacking.scale-attributes` | Which of the attributes above are multiplied by the stack size. A stack of 10 spawners with `spawn-amount` 3 spawns 30 mobs at once. `spawn-interval` and `player-range` are usually left out — a stack spawns more at once, it doesn't spawn faster or reach further. |

# Required Level 1

Every spawner type should have level `1`. Newly placed spawners start at that level unless placed
from an already-leveled item.

# Disabling an Upgrade

If you don't want players to raise a particular attribute at all, keep its value the same across
every level instead of removing the attribute — every level must still declare all five
attributes.

# Period Amount

The period length is configured in `config.yml` under the period limit settings. If the period is
disabled, the Spawns During Period attribute no longer limits spawning.

# Upgrading From an Old `levels.yml`

Servers upgrading from a version that used five separate upgrade tracks in `levels.yml` get a
`spawners.yml` generated automatically the first time they start the new version, carrying over
their old per-track values and costs. The old `levels.yml` is left on disk afterward as a
reference only — nothing reads it again, and it can be deleted once you've confirmed the generated
`spawners.yml` looks right.
