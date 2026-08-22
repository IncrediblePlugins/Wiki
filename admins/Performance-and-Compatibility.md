This page explains settings that affect performance and compatibility.

# Paper Move Event
If you use Paper, make sure `hopper.disable-move-event` is set to `false` in Paper's config.

UpgradeableHoppers needs the hopper move event to replace vanilla hopper movement with its own transfer system. If Paper disables that event, hopper transfer interception will not work correctly.

# Transfer and Suction Intervals
Each hopper type has its own `ticks.transfer` and `ticks.suction` values in `hoppers.yml`.

20 ticks are one second. Lower values make hoppers run more often. Higher values reduce how often they run.

Values below 10 ticks are raised to 10 while loading `hoppers.yml`.

Do not set these aggressively low unless you understand the server impact. The plugin is designed to batch work, but every hopper still needs periodic transfer and suction checks.

# Redstone
`optimization.redstone.pause-on-signal` makes powered hoppers stop transferring items.

`optimization.redstone.update-signal.enabled_2` controls whether hoppers and linked containers update redstone output.

`optimization.redstone.update-signal.precise` controls whether the signal is updated on every item change. Keeping this disabled is better for performance, but it may make redstone storage displays less precise.

# Full Cooldown
`optimization.full-cooldown` puts an item and link combination on cooldown when that destination cannot accept the item.

This helps prevent repeated checks against full containers, especially on servers with fast transfer intervals.

# Inventory Sync
`optimization.inv-sync` keeps linked inventory state synchronized.

Keep this enabled if other plugins modify containers, such as custom chest or storage plugins.

# Item Stackers
If your server uses WildStacker, RoseStacker, or zItemStacker, set `integration.item-stacker` to the matching provider.

This lets UpgradeableHoppers read stacked item amounts correctly during suction.

# Item Pickup Event
`integration.call-item-pickup-event` makes UpgradeableHoppers call `HopperItemPickupEvent` before a hopper picks up a dropped item.

Only enable this if another plugin needs to listen to that event.

# ShopGUIPlus
If ShopGUIPlus is installed, UpgradeableHoppers cancels selling tagged upgradeable hopper items through ShopGUIPlus.

This prevents hopper item metadata from being lost during shop transactions.

# Supported Region Plugins
UpgradeableHoppers can integrate with Lands, SuperiorSkyblock2, BentoBox, PlotSquared, and WorldGuard for placement, trust, and linking restrictions.

The Lands integration can also provide a land or nation level requirement for the number of upgradeable hoppers in claims.
