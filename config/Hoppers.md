This page explains the `hoppers.yml` file.

# Reloading
`hoppers.yml` can't be reloaded with `/upgradeablehoppers admin reload`. Restart the server after changing hopper types, levels, recipes, tick intervals, permissions, or link types.

# Hopper Types
Each entry under `hoppers` defines one hopper type. The default file includes `normal` and `chunk`.

Important options:
* `type` - `NORMAL` or `CHUNK`.
* `default` - used when players run `/upgradeablehoppers get` without a type.
* `name` - display name of this hopper type.
* `item` - item name, lore, and material for hopper items.
* `cost` - purchase cost for `/upgradeablehoppers get`.
* `ticks.transfer` - how often this hopper transfers items.
* `ticks.suction` - how often this hopper checks for dropped items.
* `recipe` - optional crafting recipe.
* `linktypes` - list of allowed destination container materials. If no list is configured, all containers are allowed.
* `suction.direct` - whether dropped items in range should be inserted directly.
* `suction.particle` - particle shown when items are sucked in. Set it to an empty string to disable it.
* `permission` - optional permission required to buy or receive this hopper type through `/upgradeablehoppers get`.

Hopper type names should be 32 characters or shorter.

To restrict link targets, configure `linktypes` as a YAML list:

````yaml
linktypes:
  - CHEST
  - BARREL
  - FURNACE
````

Use `linktypes: 'ALL'` or leave it unrestricted to allow all containers.

# Levels
Each hopper type can configure these level categories:
* `transfer_amount` - how many items are transferred per cycle.
* `suction_radius` - pickup radius. For chunk hoppers, this is a chunk radius.
* `links_amount` - maximum linked destination containers.
* `link_distance` - maximum distance from hopper to destination. Use `-1` for unlimited.

Each level has:
* `value` - the value unlocked by this level.
* `cost` - upgrade cost to reach this level.

If a level category is missing, the plugin falls back to a default value and logs a warning.

For chunk hoppers, suction radius is capped to the server view distance.

Transfer and suction tick values below 10 are raised to 10 while loading this file.

# Configure Crafting Recipe
Add a recipe to let players craft a hopper type. Example:

````yaml
# Each line represents a line in the crafting table.
# Each line must have three items. Each item must be separated by a comma.
recipe:
  - 'IRON_INGOT,CHEST,IRON_INGOT'
  - 'IRON_INGOT,REDSTONE,IRON_INGOT'
  - 'AIR,IRON_INGOT,AIR'
````
