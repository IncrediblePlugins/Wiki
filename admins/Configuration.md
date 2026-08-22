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

If you migrate between SQLite and MySQL, use `/upgradeablehoppers admin migratedb <mysql | sqlite>` after configuring the target database connection. After migration, enable the new database type in `config.yml` and restart the server.

# Commands
`command.get-confirm` controls whether players need to confirm purchases made with `/upgradeablehoppers get`.

Command aliases can be changed in the `command.alias` section. Alias changes require a restart.

# Hopper Settings
`hopper.only-owner` controls whether hopper items can only be placed by the player stored on the item. Admins can give unbound hopper items with `/upgradeablehoppers admin give <player> <type> <amount> false`.

`hopper.item.over-max` controls whether players can buy hopper items after they already reached their placed hopper limit.

`hopper.vanilla.crafting`, `hopper.vanilla.placing`, and `hopper.vanilla.convert` control how normal vanilla hoppers behave. You can allow them, block them, or convert placed vanilla hoppers into upgradeable hoppers.

`hopper.default-settings_list` can enable default hopper flags for newly placed hoppers. Valid values are:
* `FILTER_DELETE`
* `FILTER_BLACKLIST`
* `INSERT_BY_ORDER`

`hopper.teleportation.cost_2` controls the cost for teleporting to a hopper through the hopper list menu.

`hopper.upgrade-perm` enables extra upgrade permissions. If enabled, players need the matching `uhoppers.upgrade.<attribute>` permission for each upgrade type, such as `uhoppers.upgrade.TRANSFER_AMOUNT`.

The current upgrade menu checks these per-attribute permissions. Granting only `uhoppers.upgrade` is not enough for this check.

# Teleportation
`teleport.costs` controls the general teleportation cost.

`teleport.first-join_time` can make teleportation free for new players for a configured time.

`teleport.wait` controls the wait time before teleporting.

# Protection
`protection.enabled_3` protects hoppers from other players. If disabled, everyone can open, upgrade, and remove hoppers.

`protection.anti-explosive` controls whether explosions can destroy upgradeable hoppers.

`protection.allow-region-members` lets trusted members of supported region plugins open and upgrade hoppers in the same region. Deleting hoppers still requires ownership or bypass permission.

# Links and Filters
`link.whitelist` controls the default filter mode for new links.

`link.strict` controls whether new links use strict filtering by default.

`integration.prevent-untrusted-link` blocks players from linking containers or sucking items in regions where they are not trusted. This requires a restart.

# Lands Integration
`integration.lands.only-land` requires players to place hoppers inside supported claim or island regions.

`integration.lands.untrust-remove` removes or schedules removal of affected hoppers when their owner is untrusted from a supported region.

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
