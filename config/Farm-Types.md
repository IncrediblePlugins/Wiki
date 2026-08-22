# Farm Types

Farm types are configured in `farms.yml` under `types`.

Most farm-type changes should be made while the server is stopped, followed by a restart. Existing placed farms store their current level values and may not update cleanly if a type is removed or heavily restructured while the server is running.

At least one farm type must be enabled and valid. BetterFarming disables itself on startup if no farm types are configured.

# Type Key and Name

Each entry under `types` has a key:

```yaml
types:
  crop:
    enabled: true
    name: "&eCrop Farm"
```

The key is used for the generated limit ID, such as `player_farms_crop`.

The player command uses the display name with spaces replaced by dashes and color removed. For example, `name: "&eCrop Farm"` is obtained with:

`/farm get Crop-Farm`

Names are case-insensitive.

The first enabled farm type that loads successfully becomes the default type for `/farm get` when no type is entered.

# Farm Mode

`type` controls the farm behavior:

| Type | Use it for |
| --- | --- |
| `NORMAL` | Crops or blocks that BetterFarming grows by age or interval. |
| `TREE` | Saplings and tree-like growth handled through tree growth events. |

# Item

`item` defines the farm item given by `/farm get` and `/farm admin give`.

The item supports names, lore, materials, custom heads, custom model data, and compatible custom item providers used by PluginFramework.

# Farmland

`farmland` controls whether BetterFarming replaces the ground around the farm.

Set it to `AIR` to disable farmland creation.

The replacement filter is configured in `config.yml` under `farm.creation.farm-land.filter`.

# Cost and Economy

`cost` is the price of one farm item from `/farm get`.

The active economy comes from `config.yml`: Vault, experience, levels, or item currency.

# Fuel

Enable `fuel` if farms should pause when they run out of time.

```yaml
fuel:
  enabled: true
  initial: 6h
  max: 7d
  items:
    bone_meal:
      material: "BONE_MEAL"
      strict: false
      data:
        seconds: 25
```

`initial` is the fuel time a new farm starts with. `max` is the maximum stored fuel time. Each fuel item adds the configured number of seconds per item.

If `strict` is true, the item name and lore must match too. Otherwise, BetterFarming compares the item more loosely.

# Levels

Farm levels define upgrade paths.

BetterFarming supports these level types:

| Level | What it controls |
| --- | --- |
| `interval` | Seconds between growth cycles. Lower values are better, so they are sorted from slowest to fastest. |
| `storage` | Internal storage slots. |
| `radius` | Horizontal farm radius. |

Each level key must be unique. The first sorted level is used for newly created farm items.

```yaml
levels:
  interval:
    1:
      value: 120
      cost: 0
    2:
      value: 60
      cost: 7500.0
  storage:
    1:
      value: 9
      cost: 0
  radius:
    1:
      value: 1
      cost: 0
```

# Growth

`growth.visualization.enabled` controls whether BetterFarming visually updates block growth stages.

`growth.visualization.instant` controls whether visual growth updates happen immediately.

`growth.stages` controls whether crops use multiple growth stages. If enabled, total time until harvest is based on the interval and the crop's stages.

# Owner Online Requirement

`require-owner-online` pauses farms of this type while their owner is offline.

# World Blacklist

`world-blacklist` blocks a specific farm type from being placed in listed worlds.

The global list of worlds where any farm can be created is configured in `config.yml` under `general.worlds_list`.

# Recipe

Use `recipe` to allow players to craft a farm item.

```yaml
recipe:
  - "IRON_INGOT,CHEST,IRON_INGOT"
  - "IRON_INGOT,REDSTONE,IRON_INGOT"
  - "AIR,IRON_INGOT,AIR"
```

Use an empty list to disable crafting.

# Minion NPC

If `minion.enabled` is true, BetterFarming places the configured armor stand instead of the farm block.

```yaml
minion:
  enabled: true
  helmet: "skin:925a32560831c295b00527926255e608a039776f3523b92edf788149aae67d6a"
  chestplate: "LEATHER_CHESTPLATE"
  leggings: "LEATHER_LEGGINGS"
  boots: "LEATHER_BOOTS"
  tool: "IRON_HOE"
```

# Harvestable Blocks

`blocks` defines what the farm can track, grow, and harvest.

The section key is used as the material unless you set `block`.

```yaml
blocks:
  carrots:
    item:
      name: ""
      material: "CARROT"
    harvest:
      carrot:
        name: ""
        material: "CARROT"
        data:
          min: 1
          max: 1
          chance: 100
```

`item` is the item players place or plant. `harvest` is the list of item drops the farm adds to storage when the block is harvested.

`min` and `max` randomize the drop amount. `chance` controls the drop chance.

Set a harvest item to `enabled: false` to disable that drop. For enabled harvest items, chance values are treated as percentages.

# Custom Items and Model Data

You can apply custom model data, names, lore, enchantments, and custom heads to farm items, fuel items, planted items, and harvest drops.

Example custom head harvest:

```yaml
blocks:
  somehead:
    block: "PLAYER_HEAD"
    item:
      name: "Pineapple"
      material: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNTdjNWU5MjVhOTQ5ZTU1ZGIyYzI1ZWZhYWQ2NDUxMmViNmRhYjc0YWZmYjJlOWYzMDRjMzg1YjRmNGIzMGJhNSJ9fX0="
    harvest:
      pineapple_slice:
        name: "Pineapple Slice"
        material: "PAPER"
        model-data: 1000
        data:
          min: 1
          max: 4
```

General item options are documented in [GUI Menus](https://wiki.incredibleplugins.com/general/gui-menus/gui-menus).
