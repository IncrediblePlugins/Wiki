# Configuration

BetterFarming stores its files in `/plugins/BetterFarming`.

Most player-facing behavior is configured through these files:

| File | Use it for |
| --- | --- |
| `config.yml` | Language, enabled worlds, database, economy, GUI options, command aliases, farm placement, protection, hopper output, holograms, teleportation, and logging. |
| `farms.yml` | Farm types, farm items, harvestable blocks, drops, fuel, levels, recipes, world blacklists, and growth behavior. |
| `roles.yml` | Default role names and role flags for farms. |
| `player-limits.yml` | Permission-based farm limits, trusted-member limits, and playtime rewards. |
| `definitions_gui.yml` | Java inventory menu slots, materials, and shared GUI item definitions. |
| `definitions_gui-bedrock.yml` | Bedrock form menu definitions. |
| `Language/` | Messages, GUI text, dialogs, and translations. |

# Database

SQLite is used by default. Enable MySQL in `config.yml` under `database.mysql.enabled` if you want BetterFarming to use MySQL.

Use a unique `table-prefix` if BetterFarming shares a database with other plugins.

To migrate data, use `/farm admin migratedb mysql` or `/farm admin migratedb sqlite`, then enable the target database type in `config.yml` and restart the server. Make a backup before migrating.

# Economy

BetterFarming can use Vault, player experience, player levels, or item currency. If all external economy options are disabled or unavailable, item currency is used.

Farm purchase costs are configured per farm type in `farms.yml`. Upgrade costs are configured in each farm type's `levels` section.

# Placement

Important placement settings:

| Setting | Effect |
| --- | --- |
| `general.worlds_list` | Worlds where farms can be created. This requires a restart. |
| `types.<type>.world-blacklist` in `farms.yml` | Blocks one farm type from specific worlds. |
| `farm.creation.only-owner` | Only the owner stored on a farm item can place it. |
| `farm.creation.farm-land` | Lets BetterFarming create farmland under the farm area. |
| `integration.lands.only-land` | Requires farms to stay inside claims when Lands integration is used. |

Farm radius upgrades can also fail if the larger farm would overlap another farm, leave a required claim, or reach into a claim where the player is not trusted.

# Protection

`farm.protection.y-plus` and `farm.protection.y-minus` define the vertical protection area around a farm. The horizontal size comes from the farm's radius level.

`farm.protection.anti-explosive` protects farm blocks from explosions.

`farm.protection.allow-region-members` controls whether members from supported region plugins can use farms in their claims. Supported providers include Lands, SuperiorSkyblock2, BentoBox, PlotSquared, GriefPrevention, and WorldGuard, depending on the installed plugins and provider support.

When a supported protection is deleted or a player is untrusted from a protection that contains their farm, BetterFarming can remove affected farms. For normal claim deletion, `integration.lands.only-land` decides whether claim removal should also remove farms in that claim.

# Integrations

Optional integrations:

| Integration | Purpose |
| --- | --- |
| Vault | Money economy for farm purchases and upgrades. |
| Lands and other region plugins | Placement checks and optional region-member access. |
| UpgradeableHoppers | Moves harvested items from farm storage into a hopper placed directly below the farm. |
| HolographicDisplays, CMI, or DecentHolograms | Displays farm fuel or lifetime status above farms. |
| Floodgate/Geyser through PluginFramework | Bedrock-compatible menu forms where supported by the framework. |

Hopper output requires `farm.hopper.enabled` to be true. BetterFarming checks farm storage every 2 seconds and pushes items into the upgradeable hopper below the farm if one is connected and not full.

# Lands Level Requirements

When Lands is installed, BetterFarming registers a `betterfarming_farms` requirement for Lands levels if a level contains this section:

```yaml
requirements:
  betterfarming:
    farms:
      required: 5
      title: "Farms"
      description:
        - "Place farms in your land."
```

For nation levels, BetterFarming adds the farm counts from all lands in the nation.

# Reloads

Use `/farm admin reload` for normal config, language, GUI, and player-limit updates.

Restart the server after changing settings that are marked as restart-only in the files, especially database type, enabled worlds, and structural farm-type changes in `farms.yml`.
