In BetterFarming you can create an unlimited amount of custom farms. They can be added/configured in the `farms.yml` file. This page does explain various options you can configure for each farm type.

# Name
The name of the farm type. Please note that `/farm get <type>` only allows the farm type to have one word. Example: `name: 'Crop Farm'` will result in `/farm get crop`.

# Item
This item will be given to players when using `/farm get` or `/farm admin give`. If an armor stand is configured, then the armor stand will instead spawn at the placement of this block.

# Farmland
If not set to `AIR`, the farm will automatically replace the blocks at the lowest y level of the farm with this material. A filter can be configured in `config.yml` -> `farm-land.filter`.

# Cost
The cost of one farm item. Used at `/farm get`.

# Recipe
Allow players to craft this farm type.
Example:
````yaml
recipe:
  - 'IRON_INGOT,CHEST,IRON_INGOT'
  - 'IRON_INGOT,REDSTONE,IRON_INGOT'
  - 'AIR,IRON_INGOT,AIR'
````

# Armorstand
If configured and enabled, an armor stand with the given configuration will be placed instead of the farm item. Although, the farm item will still be given at `/farm get` or `/farm admin give`.

# Fuel
Requires farms to be charged with specific items to add more fuel to them. Fuel results in time the farm will be active.\
![Fuel Example](https://i.imgur.com/1SZGbDQ.png)\
[You can also apply model-data and more.](https://github.com/Angeschossen/BetterFarming/wiki/Farm-Types#model-data)

# Levels
Each level key must be unique.

# Blocks
Here you can define which blocks should be harvestable and which items should be given at the harvest.
Example:
````yaml
carrots:
block: 'CARROTS'
item:
  name: 'Carrot'
  material: 'CARROT'
harvest:
  carrot:
    name: 'Carrot'
    material: 'CARROT'
    data:
      min: 1
      max: 1
````
Whereas the section name `carrots` is the material of the block when placed. Alternatively, you can specify a `block` option to define the block. `item` is the item that is being planted. `harvest` contains a list of items that are harvested each time a crop is read to be harvested. `min` and `max` define the minimum and maximum amount of items of this type given when harvested by the farm.

![The menu where the harvestable blocks can be viewed.](https://i.imgur.com/gGicanE.png)

This results in minimum one and maximum one carrot item at harvest. An example configuration can be found here: [Link](https://github.com/IncrediblePlugins/BetterFarming/blob/master/farms.yml)

# Model-Data, Enchantments
You can apply [mode-data](https://wiki.incredibleplugins.com/general/gui-menus/gui-menus#set-custom-model-data) and [enchantments](https://wiki.incredibleplugins.com/general/gui-menus/gui-menus#specific-enchantments) to items.

# Model Data
You can specify persistent data holders, like player heads, to generate items with model-data. This player head with a pineapple texture will generate 1-4 items named "Pineapple Slice" with the model data 1000 each time it's harvested. You can apply model-data, names, lores etc. to [fuel items](https://github.com/Angeschossen/BetterFarming/wiki/Farm-Types#fuel) as well.
````yaml
somehead:
block: 'PLAYER_HEAD'
item:
  name: 'Pineapple'
  # Custom head texture.
  material: 'eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNTdjNWU5MjVhOTQ5ZTU1ZGIyYzI1ZWZhYWQ2NDUxMmViNmRhYjc0YWZmYjJlOWYzMDRjMzg1YjRmNGIzMGJhNSJ9fX0='
harvest:
  1:
    name: 'Pineapple Slice'
    material: 'PAPER'
    model-data: 1000
    data:
      min: 1
      max: 4
````