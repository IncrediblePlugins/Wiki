Land and nation levels are configured in `levels.yml` in the folder `/plugins/Lands`. You must insert valid YAML format. To
verify your format, you can paste the content of the file in a [YAML validator](https://yaml-online-parser.appspot.com).
`/lands admin reload` only reloads `land.enabled`, `nation.enabled`, the sounds and `general.farm-multipliers`. Restart
the server after changing the levels, and to enable levels that were disabled at startup.

# How Levels Work

* A land or nation **levels up in the level menu** (`/lands menu land level`, `/nations menu nation level`) once all
  requirements of the next level are met. It pays the level's `cost` from its bank once. Nations pay from the bank of their
  capital.
* **Levels are never lost.** A land that no longer meets the requirements of its level keeps it. Only admins can lower a
  level, see [Admin Commands](#admin-commands).
* **The rewards of all reached levels add up.** A land at the third level has the rewards of the first three levels.
* The `commands` of a level run **once**, when the level is reached.
* Who may level up: players with the `level_up` role flag of the land (by default only the owner), for nations the
  `nation_edit` flag.

The order of the levels in the file is ascending, from the lowest to the highest level.

# Levels

Each level's section name is its id, for example `town`. Lands stores the id for every land and nation, so **don't rename
a level's section once lands reached it**. A land with a level that doesn't exist anymore gets the highest level (and keeps
the stored id, in case you add the level again).

```yaml
land:
  enabled: true
  levels:
    town:
      name: '<dark_green>Town'
      cost: 12000
      announce: false
      titles:
        owner: 'Mayor'
        member: 'Citizen'
      requirements:
        members:
          required: 5
          title: 'Trust <v:req> Players'
          description:
            - '<t:regular>Have <v:req> players trusted.'
      rewards:
        chunks:
          value: 4
          description: '<t:regular><v:value> claims</t>'
      commands: [ ]
```

| Option | Meaning |
| --- | --- |
| `name` | Shown in menus and in front of the land's name. MiniMessage. |
| `cost` | Paid once from the bank when leveling up. `0` = free. |
| `announce` | Tell the whole server when a land or nation reaches this level. |
| `titles.owner`, `titles.member` | Titles of the owner and the members at this level, see the placeholders `%lands_land_level_title%` and `%lands_nation_level_title%`. |
| `webmap-color` | Fill color on web maps, for example `'#55FF55'`. Default: the color of the land's name. |
| `commands` | Console commands run once when the level is reached. |
| `requirements` | What a land or nation needs to level up to this level, see below. |
| `rewards` | What reaching this level gives, see below. |

In `title` and `description` of a requirement, `<v:req>` is the required value. In `description` of a reward, `<v:value>` is
the value.

## Requirements

| Requirement | Lands | Nations |
| --- | --- | --- |
| `members` | Trusted players. | Players of all lands of the nation, each player once. |
| `chunks` | Claims. | Claims of all lands. |
| `age` | Days since the land was created. | Days since the nation was created. |
| `playtime` | Hours all trusted players played together. On a network with Redis the playtime of all servers counts. | Same, for the players of all lands. |
| `tenure` | Trusted players who are trusted for at least `days` days. Temporarily trusted players don't count. | Same, over all lands. |
| `level_held` | Days since the current level was reached. | Same. |
| `lands` | - | Lands of the nation, besides the capital. |

```yaml
      requirements:
        tenure:
          required: 6
          days: 7
          title: '<v:req> Loyal Members'
          description:
            - '<t:regular>Have <v:req> players who are trusted'
            - '<t:regular>for at least 7 days.'
```

Other plugins add requirements under their own name:

```yaml
      requirements:
        upgradeablehoppers:
          hoppers:
            required: 5
            title: '<v:req> Upgradeable Hoppers'
        upgradeablespawners:
          spawners:
            required: 3
        betterfarming:
          farms:
            required: 2
```

A requirement of a plugin that isn't installed is skipped (with a warning in the console).

These plugins count blocks: a stacked spawner or hopper counts once, however many are stacked. BetterFarming loads the farms
of a world once its chunks were loaded, so right after a restart a land can have fewer farms counted than it has.

## Playtime on a Network

On a network with Redis (`database.redis` in `config.yml`), each server stores the playtime of its players in the
database, and the playtime of a player is the sum of all servers. This also counts for the playtime rewards of
`player-limits.yml`. Each server needs its own `server-name`. If your servers share the statistics files of their world
folders, set `general.playtime-shared-stats: true` in `config.yml`: then the highest playtime of the servers is used.
MultiPaper does this on its own. Without Redis, the playtime of the server is used.

## Rewards

| Reward | Lands | Nations |
| --- | --- | --- |
| `chunks` | More claims (negative: fewer). | More claims for every land of the nation. |
| `members`, `areas` | More members, sub areas. | - |
| `allies`, `enemies` | More allies, enemies. | More allies, enemies. |
| `lands` | - | More lands in the nation. |
| `upkeep` | Percent added to the upkeep, negative is a discount. Lands in a nation pay taxes instead of upkeep. | Percent added to the nation's upkeep. |
| `unlock` | Features that can only be used from this level on, see below. | Same. |
| `permissions` | Permissions the trusted players get while they're online. | Permissions the players of all its lands get. |
| `crop_growth`, `spawner_rate`, `mob_xp`, `mob_drops` | Percent bonus inside the land. | Bonus inside all its lands, on top of the land's. |
| `war_shield` | A longer war shield after a lost war, for example `6h`. | Same. |
| `effects` | - | Potion effects the nation can activate in `/nations menu nation effects`. Format `EFFECT:LEVEL`, for example `JUMP_BOOST:2`. |
| `effects_amount` | - | How many effects can be active at the same time. |

```yaml
      rewards:
        upkeep:
          value: -5
          description: '<t:regular><v:value>% upkeep cost</t>'
        unlock:
          value:
            - storage
          description: '<t:positive>+ Unlocks: <v:value></t>'
        permissions:
          value:
            - 'essentials.workbench'
        crop_growth:
          value: 10
          description: '<t:regular><v:value>% crop growth</t>'
```

### Unlocks

A feature that no level unlocks can always be used. Once a level unlocks it, lands below that level can't use it.

| Feature | What's locked below the level |
| --- | --- |
| `public_spawn` | Visitors can't teleport to the land spawn. Members can. |
| `storage` | The land storage (`/lands storage` and the main block's barrel). |
| `rentals` | Renting out and selling areas. |
| `declare_war` | Declaring wars. |

### Farm Multipliers

The farm multipliers only work if they're enabled in `general.farm-multipliers`:

```yaml
general:
  farm-multipliers:
    crop-growth: true
    spawner-rate: true
    mob-xp: true
    mob-drops: true
```

A value of `150` means one extra growth stage (or drop) and a 50% chance for a second one. Mob XP and drops only count for
mobs killed by players trusted in the land. The multipliers add up with the upgrades of BetterFarming and
UpgradeableSpawners.

## Commands

Commands run once, when a land or nation reaches the level (also if an admin sets a level higher with `commands`).

| Placeholder | Lands | Nations |
| --- | --- | --- |
| `<v:level>` | Name of the level. | Name of the level. |
| `<v:owner>` | Owner of the land. | Owner of the nation. |
| `<v:land>`, `<v:land_name>` | Command name and name of the land. | Runs the command for every land of the nation. |
| `<v:member>` | Runs the command for every trusted player. | - |
| `<v:nation>`, `<v:nation_name>` | - | Command name and name of the nation. |

```yaml
      commands:
        - 'give <v:member> diamond 1'
```

# Disabling Levels

Set `land.enabled` or `nation.enabled` to `false`. The stored levels are kept, so enabling levels again gives every land its
level back. While levels are disabled, no rewards apply and every feature is unlocked.

Levels need the `player-limits.yml` file (instead of numbered permissions for limits).

# Updating From an Older Version

A `levels.yml` from before levels were bought is converted when Lands starts:

* `title` becomes `name`.
* The `balance` requirement becomes the `cost`. Nations used to need the balance of all their lands together; now the
  capital pays it alone, so check the nation costs.
* `attributes` become `rewards`. Before, each level configured its total and only the current level counted. Now rewards
  add up, so each value becomes the difference to the level below.
* `commands.reached` become `commands`, with `<v:...>` placeholders. `commands.down` are removed (levels aren't lost
  anymore); the console lists the removed commands.

Lands keep their levels. Nobody is charged and no commands run again.

# Admin Commands

| Command | What it does | Permission |
| --- | --- | --- |
| `/lands admin land <land> level <level> [commands]` | Sets the level of a land, up or down, without paying. With `commands: true`, the commands of the levels passed upwards run and the members are told. | `lands.admin.command.land.level` |
| `/nations admin nation <nation> level <level> [commands]` | The same for a nation. | `nations.admin.command.nation.level` |

Lowering a level takes the rewards of the levels above away: limits shrink (nothing is unclaimed or untrusted), unlocked
features are locked again and nation effects that aren't unlocked anymore are turned off.

# Placeholders

See [PlaceholderAPI Placeholders](PlaceholderAPI-Placeholders.md): `%lands_land_level%`, `%lands_land_level_next%`,
`%lands_land_level_cost%`, `%lands_land_level_ready%`, `%lands_land_level_title%` and the `nation` versions.
