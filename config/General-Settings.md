# General Settings

This page explains the main `config.yml` settings that affect gameplay.

## General

| Option | Description |
| --- | --- |
| `general.language` | Default locale used by the plugin. |
| `general.worlds_list` | Worlds where upgradeable furnaces can be placed. |
| `general.eco-format` | Number and currency formatting for economy displays. |
| `general.date-format` | Date and time formatting for plugin messages. |

## Teleportation

The `teleport` section controls teleports started by FasterFurnaces menus.

| Option | Description |
| --- | --- |
| `teleport.costs` | General teleportation cost. |
| `teleport.first-join_time` | Time after first join during which teleport costs are waived. |
| `teleport.wait` | Delay before teleporting, in seconds. |

Players also need the teleport permission documented in [Permissions](../permissions/Permissions.md).

## Vanilla Furnace Behavior

| Option | Description |
| --- | --- |
| `vanilla.convert` | Converts normal furnace, blast furnace, and smoker placements into upgradeable furnaces when possible. |
| `vanilla.place` | Allows players to place normal vanilla furnace blocks. |

If `vanilla.convert` is enabled, placement can still fail when a player has reached their furnace limit or cannot place upgradeable furnaces in that location.

## Claim and Region Integrations

The `integration.lands` section is used for claim or region providers supported by the plugin, such as Lands, SuperiorSkyblock2, IridiumSkyblock, and BentoBox.

| Option | Description |
| --- | --- |
| `integration.lands.only-land` | Requires upgradeable furnaces to be placed inside claimed regions. |
| `integration.lands.untrust-remove` | Removes a player's furnaces from a region when that player is untrusted from the region. |

If `only-land` is enabled and a claim is removed, furnaces inside it are removed and returned or dropped according to the plugin's normal removal behavior.

## Economy

FasterFurnaces can charge players for getting furnace items and buying upgrades.

Economy providers are configured under `integration.economy`:

| Provider | Description |
| --- | --- |
| `vault` | Uses a Vault-compatible economy plugin. |
| `exp` | Uses player experience. |
| `level` | Uses player levels. |
| `items` | Uses item currency when other economy types are disabled or unavailable. |

If all economy providers are disabled or unavailable, item currency is used.
