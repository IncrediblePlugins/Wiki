To assign permissions to players you must install a permissions plugin, like [Luckperms](https://www.spigotmc.org/resources/28140). Below you find a list of permissions that you can assign to players or their permission groups. Please note that if a player has `/op`, they will have all permissions.

# Player Permissions
These permissions are safe to set for your players.

## Numbered Permissions
Important: 
* **Replace `<number>` with an actual number.** Example: `uhoppers.hoppers.<number>` -> `uhoppers.hoppers.5`

`uhoppers.hoppers.<number>`\
How many upgradeable hoppers can a player place? Replace `number` with an actual number.

`uhoppers.links.<number>` may appear in `plugin.yml`, but current link limits are controlled by the `links_amount` levels in `hoppers.yml`.

## Player Commands
See here: [Link](../../players/Commands.md)

`uhoppers.command.confirmtp`\
Allow using `/upgradeablehoppers confirmtp` to confirm unsafe teleport destinations.

## Hopper Type Permissions
Each hopper type in `hoppers.yml` can define its own `permission`. Players need that permission to get that hopper type with `/upgradeablehoppers get`.

## Upgrade Permissions
If `hopper.upgrade-perm` is enabled in `config.yml`, players need a permission for each upgrade type they should be allowed to buy.

The current upgrade menu checks per-attribute permissions. Granting only `uhoppers.upgrade` is not enough for this check.

`uhoppers.upgrade.TRANSFER_AMOUNT`\
Allow upgrading transfer amount.

`uhoppers.upgrade.SUCTION_RADIUS`\
Allow upgrading suction radius.

`uhoppers.upgrade.LINKS_AMOUNT`\
Allow upgrading link amount.

`uhoppers.upgrade.LINK_DISTANCE`\
Allow upgrading maximum link distance.

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

`uhoppers.admin.command.migratedb`\
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
