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
| `Locale/` | Messages, GUI text, dialogs, and translations. |

# Database

SQLite is used by default. Enable MySQL in `config.yml` under `database.mysql.enabled` if you want BetterFarming to use MySQL.

Use a unique `table-prefix` if BetterFarming shares a database with other plugins.

There is no longer a dedicated command to copy existing data between SQLite and MySQL. Switching `database.mysql.enabled` in `config.yml` and restarting connects to a fresh database on the new dialect (schema created automatically) - it does not carry over data from the old one.

## Backups

Backups are dumped to `/plugins/BetterFarming/Backups`. Configure automatic backups under `database.backup` in `config.yml`:

| Setting | Effect |
| --- | --- |
| `database.backup.schedule.time` | 24-hour `HH:mm` (server-local time zone) to run the daily backup. Leave blank to disable scheduled backups. |
| `database.backup.schedule.days` | Weekday names (e.g. `monday`, `tuesday`) to restrict the schedule to. Leave empty to back up every day. |
| `database.backup.max_backups` | How many backups to keep. Older backups beyond this count are deleted automatically. Defaults to `14`. |

You can also trigger a backup on demand with `/farm admin database backup`, independent of the schedule.

To restore a backup, use `/farm admin database restore <backup> confirm`. On SQLite, the live database file is replaced (the previous file is kept alongside it as a `.pre-restore-<timestamp>` backup). On MySQL, the target tables must already be empty - the restore does not delete existing data itself, it only fails if any target table still has rows. Either way, the server restarts immediately afterward, since the in-memory farm/player data from before the restore is never reloaded.

# Auto-Sell

Players can toggle their own farms to automatically sell harvested items instead of storing them or using a hopper, per farm from the storage menu - see [Farm Types](../config/Farm-Types.md) for the per-item `sell-price` setting that makes an item eligible, and [Admin Flags](Flags.md) for the `AUTO_SELL` toggle permission. Server-wide timing/notification behavior is configured in `config.yml` under `farm.auto-sell`:

| Setting | Effect |
| --- | --- |
| `farm.auto-sell.interval` | How often, in seconds, auto-sell runs and sells eligible farms' storage. Defaults to `30`. |
| `farm.auto-sell.notify` | Whether an online owner gets a message when their items are auto-sold. Defaults to `false`. |

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
| `integration.region.only-claimed` | Does **not** restrict initial placement - it requires a radius-growing upgrade's newly-covered area to be inside a claim, and (see Protection below) also controls whether unclaiming land deletes the farms standing in it. |

A radius-growing upgrade (not the initial placement) can fail if the larger farm would overlap another farm or reach into a claim where the player is not trusted; with `integration.region.only-claimed` enabled, it can also fail if the newly-covered area isn't inside a claim at all.

# Protection

`farm.protection.y-plus` and `farm.protection.y-minus` define the vertical protection area around a farm. The horizontal size comes from the farm's radius level.

`farm.protection.anti-explosive` protects farm blocks from explosions.

`protection.allow-region-members` controls whether members from supported region plugins can use farms in their claims. Supported providers include Lands, SuperiorSkyblock2, BentoBox, PlotSquared, GriefPrevention, and WorldGuard, depending on the installed plugins and provider support.

When a supported protection is deleted or a player is untrusted from a protection that contains their farm, BetterFarming can remove affected farms. `integration.region.only-claimed` gates unclaim-triggered removal (see Placement above), and `integration.region.untrust-remove` (defaults to `true`) gates untrust-triggered removal.

# Integrations

Optional integrations:

| Integration | Purpose |
| --- | --- |
| Vault | Money economy for farm purchases and upgrades. |
| Lands and other region plugins | Placement checks and optional region-member access. |
| UpgradeableHoppers | Moves harvested items from farm storage into a hopper placed directly below the farm. Not used by farms with auto-sell enabled - see [Auto-Sell](#auto-sell) above. |
| HolographicDisplays, CMI, or DecentHolograms | Displays farm fuel or lifetime status above farms. |
| Floodgate/Geyser through PluginFramework | Bedrock-compatible menu forms where supported by the framework. |
| PlaceholderAPI | Farm count, status, and fuel/storage placeholders - see [Placeholders](#placeholders) below. |

## Placeholders

| Placeholder | Value |
| --- | --- |
| `%betterfarming_farm_count%` | Number of farms the player owns. Add `_options{type=<farm-type-key>}` to count only one farm type. |
| `%betterfarming_paused_count%` | Number of the player's farms that are not currently running. |
| `%betterfarming_storage_full_count%` | Number of the player's farms with full storage. |
| `%betterfarming_here_status%` | Status of the farm at the player's current location, or empty if they're not standing in one. |
| `%betterfarming_here_owner%` | Owner name of the farm at the player's current location. |
| `%betterfarming_here_fuel_percent%` | Remaining fuel percentage of the farm at the player's current location. |
| `%betterfarming_here_storage_percent%` | Storage fill percentage of the farm at the player's current location. |

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
