This page explains the `hoppers.yml` file.

# Reloading
`hoppers.yml` can't be reloaded with `/upgradeablehoppers admin reload`. Restart the server after changing hopper types, levels, recipes, tick intervals, permissions, or link types.

# Hopper Types
Each entry under `types` defines one hopper type. The default file includes `normal` and `chunk`.

Important options:
* `type` - `NORMAL` or `CHUNK`.
* `name` - display name of this hopper type.
* `item` - the vanilla material used for hopper items of this type (e.g. `HOPPER`). The item's own name/lore/model-data come from the GUI locale's physical-item template, not from here.
* `cost` - purchase cost for `/upgradeablehoppers get`.
* `ticks.transfer` - how often this hopper transfers items.
* `ticks.suction` - how often this hopper checks for dropped items.
* `recipe` - optional crafting recipe.
* `linktypes` - list of allowed destination container materials. If no list is configured, all containers are allowed.
* `suction.direct` - whether dropped items in range should be inserted directly.
* `suction.particle` - particle shown when items are sucked in. Set it to an empty string to disable it.
* `permission` - optional permission required to buy or receive this hopper type through `/upgradeablehoppers get`.
* `stacking.max` - maximum stack size for this type. See [Configuration](../Configuration.md#block-stacking) for the general stacking settings.
* `stacking.scale-attributes` - which of this type's level attributes are multiplied by its stack size.

The type used when a player runs `/upgradeablehoppers get` without specifying one is whichever type is declared first in this file - move a type above `normal` to make it the default instead.

Hopper type keys (`normal`, `chunk`, ...) and custom names players set through the hopper menu should be 32 characters or shorter.

To restrict link targets, configure `linktypes` as a YAML list:

````yaml
linktypes:
  - CHEST
  - BARREL
  - FURNACE
````

Use `linktypes: 'ALL'` or leave it unrestricted to allow all containers.

# Levels
A hopper has a single, combined level - there's no separate purchase per attribute anymore. Each entry under `levels` is one numbered level (`1`, `2`, `3`, ...), and every attribute below upgrades together as part of it:

```yaml
levels:
  1:
    name: "I"
    cost: 0
    attributes:
      transfer-amount:
        value: 8
      suction-radius:
        value: 2
      links-amount:
        value: 1
      link-distance:
        value: 100
  2:
    name: "II"
    cost: 13500.0
    attributes:
      transfer-amount: { value: 11 }
      suction-radius: { value: 3 }
      links-amount: { value: 2 }
      link-distance: { value: 125 }
```

Each level has:
* `name` - display name for this level (e.g. Roman numerals like `"I"`, `"II"`).
* `cost` - the cost to purchase this level from the previous one.

Each level's `attributes` section can configure:
* `transfer-amount` - how many items are transferred per cycle.
* `suction-radius` - pickup radius. For chunk hoppers, this is a chunk radius.
* `links-amount` - maximum linked destination containers.
* `link-distance` - maximum distance from hopper to destination. Use `-1` for unlimited.

You don't need to raise every attribute by the same amount at every level - the shipped default file leaves some attributes unchanged for several levels in a row, simply by repeating the same `value`. You can add as many levels as you want.

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
