This page explains the most important admin options in `config.yml`.

# Worlds
`general.worlds_list` controls where upgradeable hoppers can be placed.

Add every world in which players should be allowed to place hoppers. You can use `*` to allow all worlds.

# Language and Formatting
`general.language` controls the default language.

`general.date-format` controls date and time output. These settings require a restart.

`general.eco-format` controls how economy values are displayed. This setting requires a restart.

# Numbered Permission Handling
`general.permission-stacking` controls how numbered permissions such as `uhoppers.hoppers.<number>` are calculated.

If disabled, the highest permission value is used. If enabled, values are added together.

Example: `uhoppers.hoppers.5` and `uhoppers.hoppers.2` give a limit of 5 when disabled, or 7 when enabled.

# Database
UpgradeableHoppers uses SQLite by default. Enable `database.mysql.enabled` if you want to use MySQL instead.

If you migrate between SQLite and MySQL, use `/upgradeablehoppers admin database migrate <mysql | sqlite>` after configuring the target database connection. After migration, enable the new database type in `config.yml` and restart the server.

## Backups
`database.backup.schedule.time` (24h `HH:mm`, server-local time zone) controls when scheduled backups run. Leave it blank (`''`) to disable scheduled backups entirely - you can still create one on demand with `/upgradeablehoppers admin database backup`.

`database.backup.schedule.days` controls which weekdays the schedule applies to. Leave it empty to back up every day.

`database.backup.max_backups` controls how many backups are kept. The oldest backups beyond this count are deleted automatically. Defaults to 14.

Backups are written to `Data/Backups/`. Restore one with `/upgradeablehoppers admin database restore <file>` - see [Commands](Commands.md) for details, including the automatic restart after a restore completes.

# Commands
`command.get-confirm` controls whether players need to confirm purchases made with `/upgradeablehoppers get`.

Command aliases can be changed in the `command.alias` section. Alias changes require a restart.

# Hopper Settings
`hopper.vanilla.crafting` controls whether normal, non-upgradeable hoppers can still be crafted. This can be bypassed with the `uhoppers.bypass.vanilla.craft` permission.

`hopper.default-settings_list` can enable default hopper flags for newly placed hoppers. Valid values are:
* `FILTER_DELETE`
* `FILTER_BLACKLIST`
* `INSERT_BY_ORDER`

`hopper.teleportation.cost_2` controls the cost for teleporting to a hopper through the hopper list menu.

`hopper.upgrade-perm` restricts who can upgrade a hopper. If enabled, players need the `uhoppers.upgrade` permission on top of ownership/trust to purchase an upgrade at all. Hoppers use a single combined level now (see below), so this is one flat permission, not a per-attribute one.

# Vanilla Hopper Placement
These two top-level options control what happens with plain vanilla hoppers - not the plugin's own upgradeable ones:

`vanilla.place` controls whether a plain vanilla hopper can be placed at all when it isn't auto-converted.

`vanilla.convert` controls whether placing a plain vanilla hopper automatically converts it into a real upgradeable hopper instead.

# Block Stacking
Several upgradeable hoppers of the same type and level can share a single physical block, with a bigger transfer amount and link count. This is disabled by default - see the new `stacking` section in `config.yml`, and each hopper type's own `stacking` section in `hoppers.yml`, for the full set of options and their defaults.

`stacking.merge-radius` controls automatic merging of newly placed hoppers with a nearby compatible stack. This ships at `0` (disabled) for hoppers specifically - hoppers are routinely placed directly next to each other on purpose (a row of hoppers, each with its own separate links), so auto-merging on placement would silently combine hoppers that were never meant to be one stack. Players can still stack manually: hold a matching hopper item and click the "stack" item in a hopper's menu.

`stacking.max-stack` caps how many hoppers can share one block, server-wide. A type's own `hoppers.yml` `stacking.max` can lower this further per type - set it to `1` to stop that type from stacking at all.

The `uhoppers.stack.<number>` permission can cap this further per player. Without it, only the config caps above apply.

`stacking.sneak-breaks-whole` controls what a sneak-break (the only break gesture hoppers use - a plain click opens the menu instead) does to a stack: break the whole stack at once (the default), or remove just one hopper from it, leaving the rest in place.

`stacking.drop-bundled-item` controls how a broken stack is returned: as one hopper item per hopper in the stack (the default - they stack normally in a player's inventory), or as a single "bundled" item that remembers the whole amount and rebuilds the stack when placed again.

`stacking.count-towards-player-limit` controls whether every hopper inside a stack counts towards a player's placed-hopper limit, or just the one physical block.

`stacking.upgrade-cost-multiplied` controls whether the cost to upgrade a stack is multiplied by its stack amount.

# Teleportation
`teleport.costs` controls the general teleportation cost.

`teleport.first-join_time` can make teleportation free for new players for a configured time.

`teleport.wait` controls the wait time before teleporting.

# Protection
Hoppers are always owned - only the owner (and anyone they've trusted) can open, upgrade, or remove one, unless a player has a bypass permission. Players can grant other players access to their own hoppers if the ChestProtect plugin is installed.

`protection.anti-explosive` controls whether explosions can destroy upgradeable hoppers.

`protection.allow-region-members` lets trusted members of supported region plugins open and upgrade hoppers in the same region. Deleting hoppers still requires ownership or bypass permission.

# Links and Filters
`link.whitelist` controls the default filter mode for new links.

`link.strict` controls whether new links use strict filtering by default.

`integration.prevent-untrusted-link` blocks players from linking containers or sucking items in regions where they are not trusted. This requires a restart.

# Lands Integration
`integration.lands.only-land` requires players to place hoppers inside supported claim or island regions.

# Region Integration
These two options control hoppers automatically becoming claimable by someone else (shown with a "Trying to claim this hopper..." message) once their owner loses access to the region the hopper stands in - supported by Lands, SuperiorSkyblock2, BentoBox, PlotSquared, and WorldGuard.

`integration.region.only-claimed` makes a hopper claimable when the claiming-type region it stands in (e.g. a Lands claim) gets deleted or unclaimed. Region types that aren't claim-based (e.g. a WorldGuard flag region) always trigger this regardless of this setting.

`integration.region.untrust-remove` makes a hopper claimable when its owner gets untrusted from the region it stands in.

# Economy
The economy section controls whether hopper purchases and upgrades use Vault, player experience, or item currency.

`integration.economy.vault.enabled_10` uses a Vault economy plugin.

`integration.economy.exp.enabled_15` uses player experience.

`integration.economy.items.strict_2` controls strict matching for item currency.

If every economy type is disabled or unavailable, the item based economy is used.

# Skins
`general.fetch-skins-names` controls whether player skins and names are fetched from Mojang.

`integration.skins-restorer` uses SkinsRestorer for skins if `general.fetch-skins-names` is enabled.

# Visualization
`visualization.link.link-duration_time` controls how long link visualizations can stay active.

`visualization.suction.suction-duration_time` controls how long suction-radius visualizations can stay active.

# GUI, Sounds, and Logging
`gui.definitions-file` creates a shared GUI definitions file for non-locale-specific GUI settings.

`gui.max-lore-length` controls automatic lore line wrapping. Set it to `0` to disable wrapping.

The `sounds` section controls teleport and hopper sounds. Set a sound to an empty string to disable it.

`logging.debug` enables extra debug logging when support asks for it.
