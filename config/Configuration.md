# Configuration

This page explains the most important options in `config.yml`.

Some option names in the generated file include suffixes such as `_list`, `_time`, or `_2`. The
plugin reads these as the same logical setting, but you should keep the option names exactly as
they appear in your file.

# Worlds

`general.worlds_list` controls where players can place upgradeable spawners.

Use `*` to allow every world, or list only the worlds where spawners should work.

# Commands and Costs

`command.alias` controls command aliases such as `/spawners` and `/spawner`.

`command.get-confirm` controls whether players must confirm paid `/spawners get` purchases.

`spawner.item.cost` controls the price of spawner items from `/spawners get`.

The teleportation cost setting in `spawner.teleportation` controls the teleport cost used by
`/spawners list`.

# Ownership and Placement

`spawner.only-owner` makes spawner items placeable only by their stored owner.

`spawner.entity-change` controls whether the entity type item is available in the spawner menu.

`limit.max-per-chunk` limits how many upgradeable spawners can be placed in one chunk.

`integration.lands.only-land` requires supported claim or region protection before placing
spawners.

`integration.lands.allow-region-members` lets trusted region members interact with spawners if the
region provider allows it.

# Breaking and Pickup

`spawner.allowed-tools_list` controls which tools can retrieve spawners.

The `spawner.silktouch` section controls whether Silk Touch is required, the minimum enchantment
level, and the pickup chance.

`spawner.visitor-break` controls whether visitors can break unprotected spawners. Owners can always
break their own spawners.

Players with the delete bypass can ignore the Silk Touch requirement.

# Vanilla Spawners

The `spawner.vanilla` section controls normal Minecraft spawners:

| Option | Use |
| --- | --- |
| `placing` | Whether normal spawners can be placed. |
| `spawn` | Whether normal spawners can spawn entities. |
| `egg` | Whether spawn eggs can change normal or upgradeable spawners. |
| `claim` | Whether interacting with a normal spawner converts it into an upgradeable spawner. |

If normal spawner placement is disabled, `uspawners.bypass.vanilla.place` allows staff to place
normal spawners anyway.

# Limits and Performance

`limit.area.max-entities` pauses nearby upgradeable spawners when too many entities spawned by
UpgradeableSpawners are in the configured area.

The period time setting in `limit.period` controls the period used by the Spawns During Period
upgrade. Set the period to `0` to disable that limit.

`optimization.redstone.pause-on-signal` pauses upgradeable spawners while they receive redstone
power.

Butcher mode and entity stacking can reduce the number of living entities near farms.

# Economy

UpgradeableSpawners can use Vault, player experience, player levels, or item currency depending on
your economy settings and installed dependencies.

If all supported economy integrations are disabled or unavailable, item currency is used.

# Holograms

The `hologram` section controls whether spawner status holograms are shown and whether they are
only shown while a spawner is paused.

Set `general.hologram-provider` if you want to force a specific supported hologram plugin.
