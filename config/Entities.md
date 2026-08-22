# Entities

This page explains special config options in the `entities.yml` file.

# Entity Types

Each entity type can define its display name, purchase cost, menu skull, whether it is enabled, and
whether it is the default entity for `/spawners get`.

To buy a mob type in the entity menu, players need this permission:

`uspawners.mob.<mob>`

Example: `pig` uses `uspawners.mob.pig`.

# Disable Vanilla Spawn Conditions

Set `no-conditions` to `true` in the section of the entity.

This makes UpgradeableSpawners use its custom spawning logic for that entity type. Normal Minecraft
spawn conditions are ignored, but UpgradeableSpawners limits such as player range, nearby entities,
spawn interval, and spawns during period still apply.

Example:

```yaml
types:
  pig:
    name: Pig
    cost: 5000.0
    skull: skin:bee8514892f3d78a32e8456fcbb8c6081e21b246d82f398bd969fec19d3c27b3
    # '/Spawners get' will give a pig spawner. You can just remove this option and place it somewhere else to change the default entity.
    default: true
    # Should spawners of this entity type have butcher mode enabled?
    # This does save performance, since no living entities are spawned. This acts like a virtual spawner
    # that doesn't spawn any entities, but still harvests their loot.
    # If you disable this option again, then butcher mode will be set to the state each individual spawner had before
    # it was enabled.
    force-butcher:
      # Always force butcher?
      always: false
    # If you allow Bedrock players on your server and have floodgate installed, you can set an image for this entity in the Bedrock menu.
    # More information: https://github.com/Angeschossen/PluginFrameworkAPI/wiki/Bedrock-Menus#button-icons
    bedrock-image: ''
    # Should this entity type use UpgradeableSpawners' custom spawning?
    # Normal Minecraft spawn conditions are ignored, but UpgradeableSpawners limits still apply.
    # NOTE: This option requires server reload / restart.
    no-conditions: true
```

# Custom Drops

You can define custom item and experience drops. By default, these drops are additive and don't
replace the current ones.

To make them replace the current ones, add `replace: true` to the drops section:

```yaml
  blaze:
    name: Blaze
    cost: 5000.0
    skull: skin:b78ef2e4cf2c41a2d14bfde9caff10219f5b1bf5b35a49eb51c6467882cb5f0
    drops:
      replace: true # replaces existing default drops
      items:
        blaze_rod:
          material: BLAZE_ROD
```

## Custom Item Drops

You can define custom item drops by adding an `items` list to the `drops` section.

```yaml
  blaze:
    name: Blaze
    cost: 5000.0
    skull: skin:b78ef2e4cf2c41a2d14bfde9caff10219f5b1bf5b35a49eb51c6467882cb5f0
    drops:
      items:
        blaze_rod:
          material: BLAZE_ROD
          data:
            chance: 50 # has a 50% chance of dropping
            min: 1 # minimum 1 blaze rod
            max: 2 # maximum 2 blaze rods
```

You can also apply more item parameters as seen here:
[Optional Item Parameters](https://wiki.incredibleplugins.com/general/gui-menus/gui-menus#optional-item-parameters).

## Custom Experience Drop

You can define custom exp drops by adding an `exp` option to the `drops` section.

```yaml
  blaze:
    name: Blaze
    cost: 5000.0
    skull: skin:b78ef2e4cf2c41a2d14bfde9caff10219f5b1bf5b35a49eb51c6467882cb5f0
    drops:
      exp: '50:1:1' # has a 50% chance of dropping minimum and maximum 1 experience orb
```

# Force Butcher Mode

Use `force-butcher.always: true` for an entity type if spawners of that type should always use
butcher mode.

Players cannot toggle butcher mode off while it is forced for the selected entity type.
