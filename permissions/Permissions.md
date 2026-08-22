# Permissions

To assign permissions to players you must install a permissions plugin, such as
[LuckPerms](https://www.spigotmc.org/resources/28140).

Players with operator status usually have every permission.

Read [Recommended Permission Setup](Recommended-Permission-Setup.md) if you want a simple starting
point.

# Player Permissions

These permissions are safe to set for players.

## Numbered Permissions

Replace `<number>` with an actual number.

Example: `uspawners.spawners.<number>` -> `uspawners.spawners.5`

`uspawners.spawners.<number>`\
Sets how many upgradeable spawners a player can have placed at once.

If `permission-stacking` is enabled in `config.yml`, multiple numbered permissions are added
together. Otherwise, the highest number is used.

## Player Command Permissions

`uspawners.command.get`\
Allows `/spawners get`.

`uspawners.command.list`\
Allows `/spawners list`.

`uspawners.command.confirmtp`\
Allows `/spawners confirmtp`.

`uspawners.command.*`\
Allows all player commands.

## Other

`uspawners.upgrade`\
Allow players with this permission to upgrade their spawners.

`uspawners.drop-item`\
Drop the spawner item when players break the spawner.

`uspawners.silktouch`\
Allows players to mine spawners with Silk Touch if Silk Touch pickup is enabled in `config.yml`.

`uspawners.mob.<mob>`\
Allow players to purchase mob types. Replace `<mob>` with a mob type from `entities.yml`.

## Teleportation

The following permissions limit teleportation initiated by UpgradeableSpawners. Players have them
by default. If teleportation is started through a command, players also need the command permission.

### Disabling Teleportation

If you want to disable a teleportation, unset the permission in your permissions plugin.

Example for LuckPerms:

`/luckperms group default permission set uspawners.teleport.spawner false`

The value `false` is important here.

### Teleportation Permissions

`uspawners.teleport.spawner`\
Allows teleportation to placed spawners via `/spawners list`. This permission is set by default.

# Admin Permissions

These permissions should only be given to staff.

## Admin Command Permissions

`uspawners.admin.command`\
Allows access to `/spawners admin`.

`uspawners.admin.command.give`\
Allows `/spawners admin give`.

`uspawners.admin.command.reload`\
Allows `/spawners admin reload`.

`uspawners.admin.command.about`\
Allows `/spawners admin about`.

`uspawners.admin.command.player`\
Allows `/spawners admin player`.

`uspawners.admin.command.teleport`\
Allows `/spawners admin teleport`.

`uspawners.admin.command.list`\
Allows `/spawners list <player>` for viewing another player's spawners.

`uspawners.admin.command.listperms`\
Allows `/spawners admin listperms`.

`uspawners.admin.command.migratedb`\
Allows `/spawners admin migratedb`.

`uspawners.admin.command.killall`\
Allows `/spawners admin killall`. This command is not registered on Folia.

`uspawners.admin.*`\
Allows all admin commands. This does not include bypass permissions.

## Bypass Permissions

`uspawners.bypass.delete`\
Allows deleting spawners that belong to other players.

`uspawners.bypass.edit`\
Allows editing and upgrading spawners that belong to other players.

`uspawner.bypass.ownership`\
Allows placing spawner items even if they belong to another player. Current placement code checks
this singular `uspawner` permission.

`uspawners.bypass.only-land`\
Bypasses claim or trusted-region placement restrictions.

`uspawners.bypass.vanilla.place`\
Allows placing normal Minecraft spawners even if normal spawner placement is disabled.

`uspawners.bypass.*`\
Allows all plural `uspawners.bypass` permissions declared by the plugin. It does not cover the
singular `uspawner.bypass.ownership` placement check.

# Wildcards

`uspawners.*` includes the permissions declared under the plugin's `uspawners` namespace. It does
not cover the current singular `uspawner.bypass.ownership` placement check.
