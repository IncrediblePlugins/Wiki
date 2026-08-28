1. Stop your server.
2. Put the plugin jar in your `plugins` folder.
3. Start your server once to generate the configuration files.
4. Stop your server again.
5. Edit the files in `/plugins/UpgradeableHoppers`.
6. If you use Paper, make sure `hopper.disable-move-event` is set to `false` in Paper's config.
7. Start your server.

Please always stop your server before installing updates. The config and locale files automatically add new entries and remove no longer existing entries.

# Important Files
`config.yml` controls general settings, database, aliases, vanilla hopper restrictions, protection, integrations, teleportation, economy, and optimization.

`hoppers.yml` controls hopper types and upgrade levels. This file can't be reloaded with `/upgradeablehoppers admin reload`; restart the server after changing it.

# Optional Dependencies
UpgradeableHoppers can hook into Vault, Lands, SuperiorSkyblock2, BentoBox, PlotSquared, WorldGuard, WildStacker, RoseStacker, zItemStacker, WildChests, AdvancedChests, and ShopGUIPlus.

Install the optional plugins you use before starting the server so UpgradeableHoppers can detect them during startup.
