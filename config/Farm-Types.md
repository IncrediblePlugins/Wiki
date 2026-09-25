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

`item` sets the material of the farm item given by `/farm get` and `/farm admin give` - a plain vanilla material name, for example `item: END_ROD`.

The item's name, lore, and other display are not configured per farm type. They come from the server's GUI locale (`Locale/<lang>_gui.yml`), under a single shared `physical: block:` template used by every farm type - the `<v:type>` placeholder in that template is what shows the specific farm type's own display name.

# Farmland

`farmland` controls whether BetterFarming replaces the ground around the farm.

Set it to `AIR` to disable farmland creation.

The replacement filter is configured in `config.yml` under `farm.creation.farm-land.filter`.

# Cost and Economy

`cost` is the price of one farm item from `/farm get`.

The active economy comes from `config.yml`: Vault, experience, levels, or item currency.

# Fuel

Add a `fuel` section if farms of this type should pause when they run out of time. The section's presence is the opt-in - there is no separate enable switch.

```yaml
fuel:
  initial-seconds: 6h
  max-seconds: 7d
  items:
    bone_meal:
      material: "BONE_MEAL"
      strict: false
      seconds: 25
```

`initial-seconds` is the fuel time a new farm starts with, seeded automatically the moment the farm item is placed. `max-seconds` is the maximum stored fuel time. Each fuel item adds its own `seconds` per item used.

If `strict` is true, the item name and lore must match too. Otherwise, BetterFarming compares the item more loosely.

## Shared Fuel Item Presets

If multiple farm types use the same fuel items, define them once under a top-level `fuel-items` section (a sibling of `types`) and reference the preset by name instead of repeating the list:

```yaml
fuel-items:
  default:
    bone_meal:
      material: "BONE_MEAL"
      strict: false
      seconds: 25

types:
  crop:
    fuel:
      items-preset: default
```

`items-preset` replaces `items` entirely for that farm type - a type using `items-preset` does not also need its own `items` list.

## Buying Fuel

Let players buy fuel time directly with their currency instead of requiring a physical fuel item:

```yaml
fuel:
  purchase:
    enabled: true
    seconds-per-unit: 1800
    cost: 100.0
```

When enabled, the fuel menu gets a purchase option that adds `seconds-per-unit` of fuel time for `cost`, using the same economy configured in `config.yml`. Purchases still respect the farm's `max-seconds` fuel cap.

## Low Fuel Warning

```yaml
fuel:
  warning-threshold-seconds: 300
```

When a farm's remaining fuel drops below `warning-threshold-seconds`, the owner gets a one-time warning if they are online. Set this to `0` to disable the warning. Defaults to `300` (5 minutes).

# Levels

A farm has one combined level per tier - radius, growth interval, and storage capacity all upgrade together as a single purchase. There is no independent-axis upgrading (buying more radius without also paying for whatever interval/storage change comes with that level).

Each level is a numbered entry under `levels`, with a display `name`, the `cost` to buy that level from the previous one, and an `attributes` map giving the value each attribute takes at that level:

```yaml
levels:
  1:
    name: '1'
    cost: 0
    attributes:
      interval:
        value: 120
      radius:
        value: 1
      storage:
        value: 9
  2:
    name: '2'
    cost: 7500.0
    attributes:
      interval:
        value: 60
      radius:
        value: 2
      storage:
        value: 18
```

The three built-in attributes:

| Attribute | What it controls |
| --- | --- |
| `interval` | Seconds between growth cycles. Lower is faster. |
| `radius` | Horizontal farm radius. |
| `storage` | Internal storage slots (only used if the type also has a `storage` section - see below). |

Level `1` (or whichever level sorts first) is what a newly created farm item starts at. A level doesn't have to change every attribute compared to the one before it - once an attribute reaches its intended maximum, later levels can just repeat its value and only grow the others, so admins aren't forced to keep paying for an attribute that's already done growing.

# Growth

`growth.visualization.enabled` controls whether BetterFarming visually updates block growth stages.

`growth.visualization.instant` controls whether visual growth updates happen immediately.

`growth.stages` controls whether crops use multiple growth stages. If enabled, total time until harvest is based on the interval and the crop's stages.

# Owner Online Requirement

`require-owner-online` pauses farms of this type while their owner is offline.

# World Blacklist

`world-blacklist` blocks a specific farm type from being placed in listed worlds.

The global list of worlds where any farm can be created is configured in `config.yml` under `general.worlds_list`.

# Storage

Add a `storage` section to give farms of this type internal storage - harvested items go here until collected or drained into a hopper. The section's presence is the opt-in; an empty section is enough:

```yaml
storage: { }
```

Storage capacity comes from the type's own `storage` level attribute (see [Levels](#levels) above), so it already grows with upgrades without any separate config number. A farm type with no `storage` section can't hold harvested items at all - pair it with auto-sell (see below) if you want harvests to go straight to currency instead.

# Hopper

Add a `hopper` section to let a connected UpgradeableHoppers hopper drain this farm type's storage automatically:

```yaml
hopper:
  y-range: 1
```

`y-range` is how many blocks below the farm's own position to look for a hopper. The section's presence is the opt-in - a type without it never queries UpgradeableHoppers at all, even if the integration is installed and enabled in `config.yml`.

# Auto-Sell

Instead of storing harvested items or draining them into a hopper, a player can toggle their farm to automatically sell eligible harvested items for currency. This is a per-farm toggle in the storage menu, not a per-type config option - the toggle only appears if at least one of the type's harvest items has a configured `sell-price` (see [Harvestable Blocks](#harvestable-blocks) below).

Auto-sell and hopper output are mutually exclusive per farm - a farm with auto-sell enabled is skipped by the hopper-drain task. How often auto-sell runs and whether owners are notified are configured in `config.yml` under `farm.auto-sell`. See [Admin Flags](../admins/Flags.md) for the `AUTO_SELL` flag and its permission.

# Stacking

Add a `stacking` section to let players stack multiple farm items of this type into one farm, instead of every farm needing its own separate spot:

```yaml
stacking:
  max: 10
  scale-attributes: [ storage, interval ]
```

Placing a compatible farm item (same type, same level) anywhere inside an existing farm's own protected area merges it into that farm - not just right next to the farm's own block - instead of being rejected as an overlap. `max` caps how many can stack at one farm, on top of `upgrade.yml`'s own global `stacking.max-stack` cap (the lower of the two applies).

`scale-attributes` lists which of the type's level attributes grow with the stack amount:

* `storage` scales up normally - a stack of 10 has 10x the storage capacity of a single farm at that level.
* `interval` scales *down* instead (growth gets faster, not slower) - a stack of 10 completes growth cycles roughly 10x faster on the same set of blocks. This is a farm-specific inversion of how stacking normally works, because a shorter interval is the better outcome for this attribute.
* `radius` is not meant to be listed here - stacking multiple farms at one point doesn't grow the protected area, only what happens inside the single area the level already grants.

Fuel isn't separately affected by stacking - because interval scales down while the farm consumes fuel each completed cycle, more frequent (but proportionally cheaper) fuel use roughly cancels out, so a stacked farm runs out of fuel in about the same real time as an unstacked one, just gets far more done in that time.

The main farm menu shows a **Stacked** item with the current/maximum stack amount once stacking is enabled for the server (`upgrade.yml`'s `stacking.merge-radius` above `0`) - see [Farm Menu](../players/Farm-Menu.md).

# Recipe

Use `recipe` to allow players to craft a farm item.

```yaml
recipe:
  - "IRON_INGOT,CHEST,IRON_INGOT"
  - "IRON_INGOT,REDSTONE,IRON_INGOT"
  - "AIR,IRON_INGOT,AIR"
```

Use an empty list to disable crafting.

# Armor Stand Representation

Add an `armor-stand` section to represent this farm type with a decorative armor stand instead of a real placed block. The section's presence is the opt-in - a custom item provider (Nexo/ItemsAdder) block or furniture configured on `item` above still takes priority over this if set.

```yaml
armor-stand:
  helmet: "skin:925a32560831c295b00527926255e608a039776f3523b92edf788149aae67d6a"
  chestplate: "LEATHER_CHESTPLATE"
  leggings: "LEATHER_LEGGINGS"
  boots: "LEATHER_BOOTS"
  tool: "IRON_HOE"
```

Every slot is optional. Off by default - the real vanilla item's own block (the `material` set on `item` above) represents the farm instead.

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
          sell-price: 0
```

`item` is the item players place or plant. `harvest` is the list of item drops the farm adds to storage when the block is harvested.

`min` and `max` randomize the drop amount. `chance` controls the drop chance.

Set a harvest item to `enabled: false` to disable that drop. For enabled harvest items, chance values are treated as percentages.

`sell-price` is the per-unit amount auto-sell pays for this item. It defaults to `0`, meaning the item cannot be auto-sold and is only ever collected manually or moved through a hopper. Set it above `0` to make the item sellable - see [Auto-Sell](#auto-sell) above.

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
