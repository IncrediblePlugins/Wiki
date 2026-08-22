# Furnaces

This page explains the `furnaces.yml` configuration file.

Changes to this file require a full server restart. Furnace types and level progressions are loaded during startup.

## Furnace Types

Each entry under `types` creates one upgradeable furnace type. The default configuration contains:

| Type | Vanilla item |
| --- | --- |
| `furnace` | `FURNACE` |
| `blast_furnace` | `BLAST_FURNACE` |
| `smoker` | `SMOKER` |

The type key is used in commands such as `/fasterfurnaces get furnace 1` and `/fasterfurnaces admin give <player> furnace 1`.

Important type options:

| Option | Description |
| --- | --- |
| `name` | Display name of the upgradeable furnace type. |
| `item` | Vanilla block material used for the placed block and item. |
| `cost` | Cost for players to get this furnace type with `/fasterfurnaces get`. |
| `flags` | Special behavior flags for this furnace type. |
| `levels` | Ordered list of upgrade levels. |

## Levels

Levels are read in the order they appear in `furnaces.yml`. Each level has a display `name`, an upgrade `cost`, and an `attributes` section.

The default setup has six levels for each furnace type. Upgrade costs increase from level to level, while cook time and fuel time improve.

## Attributes

FasterFurnaces supports these level attributes:

| Attribute | Description |
| --- | --- |
| `cook-time` | Changes smelting time by a percentage. Negative values are faster; positive values are slower. |
| `fuel-time` | Changes fuel burn time by a percentage. Positive values make fuel last longer. |
| `exp` | Changes dropped experience by a percentage. Positive values give more experience; negative values give less. |

Example:

```yaml
attributes:
  cook-time:
    value: -20
  fuel-time:
    value: 20
  exp:
    value: 0
```

This level smelts 20 percent faster, makes fuel last 20 percent longer, and keeps experience unchanged.

## Flags

You can apply special flags to furnace types in `furnaces.yml`.

| Flag | Description |
| --- | --- |
| `EXPLOSION_DAMAGE` | Allows explosions to destroy this upgradeable furnace type. If destroyed, the furnace item is dropped or returned according to the normal removal behavior. |
