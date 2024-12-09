This page explains special config options in the ``entities.yml`` file.

# Disable Vanilla Spawn Conditions
Set ``no-conditions`` to ``true`` in the section of the entity. Example:
````yaml
types:
  pig:
    name: Pig
    cost: 5000.0
    skull: skin:bee8514892f3d78a32e8456fcbb8c6081e21b246d82f398bd969fec19d3c27b3
    # '/Spawners get' will give a pig spawner. You can just remove this option and place it somewhere else to change the default entity.
    default: true
    # Should spawners of this entity type to have butcher mode enabled?
    # This does save performance, since no living entities are spawned. This acts like a virtual spawner
    # that doesn't spawn any entities, but still harvests their loot.
    # If you disable this option again, then butcher mode will be set to the state each induvidual spawner had before
    # it was enabled.
    force-butcher:
      # Always force butcher?
      always: false
    # If you allow Bedrock players on your server and have floodgate installed, you can set an image for this entity in the Bedrock menu.
    # More information: https://github.com/Angeschossen/PluginFrameworkAPI/wiki/Bedrock-Menus#button-icons
    bedrock-image: ''
    # Should a spawner, with this entity type selected, always spawn entities? That means that there are no spawn conditions, except the levels from levels.yml (except player_range).
    # All spawners will be able to spawn in air and underwater. There are no restrictions.
    # NOTE: This option required server reload / restart.
    no-conditions: true
````

# Custom Item Drops
You can define custom item drops by adding a ``items`` list as seen below. Must be placed in the ``drops`` section. If it isn't there by default, just add it as seen below.

````yaml
  blaze:
    name: Blaze
    cost: 5000.0
    skull: skin:b78ef2e4cf2c41a2d14bfde9caff10219f5b1bf5b35a49eb51c6467882cb5f0
    drops:
      items:
       - 'BLAZE_ROD:50:1:2' # has a 50% chance of dropping mimium 1 and maximum 2 blaze rods
````

# Custom Experience Drop
You can define custom exp drops by adding a ``exp`` option as seen below. Must be placed in the ``drops`` section. If it isn't there by default, just add it as seen below.

````yaml
  blaze:
    name: Blaze
    cost: 5000.0
    skull: skin:b78ef2e4cf2c41a2d14bfde9caff10219f5b1bf5b35a49eb51c6467882cb5f0
    drops:
      exp: '50:1:1' # has a 50% chance of dropping minimum and maximum one blaze rod
````