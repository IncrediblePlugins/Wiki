To assign permissions to players you must install a permissions plugin, like [Luckperms](https://www.spigotmc.org/resources/28140). Below you find a list of permissions that you can assign to players or their permission groups. Please note that if a player has `/op`, they will have all permissions.

# Player Permissions
These permissions are safe to set for your players.

## Numbered Permissions
Important: 
* **Replace `<number>` with an actual number.** Example: `uhoppers.hoppers.<number>` -> `uhoppers.hoppers.5`

`uhoppers.hoppers.<number>`\
How many upgradeable hoppers can a player place? Replace `number` with an actual number.

`uhoppers.links.<number>` may appear in `plugin.yml`, but current link limits are controlled by the `links_amount` levels in `hoppers.yml`.

`uhoppers.stack.<number>`\
Caps how many hoppers a player can stack into a single block, if [block stacking](../Configuration.md#block-stacking) is enabled. Without this permission, only `config.yml`'s `stacking.max-stack` and a type's own `hoppers.yml` `stacking.max` apply.

## Player Commands
See here: [Link](../../players/Commands.md)

`uhoppers.command.confirmtp`\
Allow using `/upgradeablehoppers confirmtp` to confirm unsafe teleport destinations.

## Hopper Type Permissions
Each hopper type in `hoppers.yml` can define its own `permission`. Players need that permission to get that hopper type with `/upgradeablehoppers get`.

## Upgrade Permissions
Hoppers use a single combined level (transfer amount, suction radius, link amount, and link distance all upgrade together in one purchase). If `hopper.upgrade-perm` is enabled in `config.yml`, players need one flat permission to buy an upgrade at all:

`uhoppers.upgrade`\
Allow upgrading a hopper's level.

## Teleportation
The following permissions limit all teleportation initiated by UpgradeableHoppers. Players have them by default. However, in some cases
the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.

### Disabling Teleportation
If you want to disable a teleportation you need to unset the permission in your permissions plugin.
Example for LuckPerms: ``/luckperms group default permission set uhoppers.teleport.hopper false``
The value `false` is important here.

### Teleportation Permissions
`uhoppers.teleport.hopper`\
Allow teleportation to hoppers through the `/hoppers list` menu. This permission is set by default.

# Admin Permissions
These permissions should only be given to staff or server admins.

## Admin Commands
See here: [Link](../Commands.md)

`uhoppers.admin.command`\
Allow using `/upgradeablehoppers admin`.

`uhoppers.admin.command.give`\
Allow giving hopper items to players.

`uhoppers.admin.command.reload`\
Allow reloading reloadable configuration files.

`uhoppers.admin.command.database`\
Allow using `/upgradeablehoppers admin database`.

`uhoppers.admin.command.database.backup`\
Allow creating an on-demand database backup.

`uhoppers.admin.command.database.restore`\
Allow restoring the database from a backup.

`uhoppers.admin.command.database.migrate`\
Allow migrating data between SQLite and MySQL.

`uhoppers.admin.command.about`\
Allow viewing debug information.

`uhoppers.admin.command.listperms`\
Allow listing detected permissions for a player.

`uhoppers.admin.command.list`\
Allow viewing another player's hopper list with `/upgradeablehoppers list <player>`.

`uhoppers.admin.command.import` may appear in `plugin.yml`, but the import subcommand is not active in the current plugin code.

## Bypass Permissions
`uhoppers.bypass.open`\
Open hoppers from other players.

`uhoppers.bypass.upgrade`\
Upgrade hoppers from other players.

`uhoppers.bypass.delete`\
Delete hoppers from other players.

`uhoppers.bypass.claim`\
Allow creating links in claims, in which the player is not trusted.

`uhoppers.bypass.only-land`\
Bypass the `integration.lands.only-land` option in `config.yml`.

`uhoppers.bypass.vanilla.craft`\
Bypass the option that denies crafting vanilla hoppers.

`uhoppers.bypass.vanilla.place`\
Bypass the option that denies placing vanilla hoppers.
