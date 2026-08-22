# Permissions

To assign permissions to players, install a permissions plugin such as [LuckPerms](https://www.spigotmc.org/resources/28140). Players with `/op` have all permissions.

## Player Permissions

These permissions are safe to give to normal players.

### Numbered Permissions
Important:

* Replace `<number>` with an actual number.
* Example: `fasterfurnaces.furnaces.<number>` becomes `fasterfurnaces.furnaces.5`.

| Permission | Description |
| --- | --- |
| `fasterfurnaces.furnaces.<number>` | Allows a player to own up to this many placed upgradeable furnaces. |
| `fasterfurnaces.members.<number>` | Allows a player to trust up to this many players to each furnace or protection entry, depending on the menu being used. |

### Command Permissions

See [Player Commands](../players/Commands.md).

### Teleportation

The following permissions control teleportation initiated by FasterFurnaces. Players have them by default. If teleportation is started through a command, the player also needs permission to use that command.

| Permission | Description |
| --- | --- |
| `fasterfurnaces.teleport.furnace` | Allows teleporting to placed furnaces from the furnace list menu. |

To disable a teleport permission, unset it in your permissions plugin.

LuckPerms example:

```text
/luckperms group default permission set fasterfurnaces.teleport.furnace false
```

The `false` value is important.

## Admin Permissions

These permissions should only be given to staff or server administrators.

| Permission | Description |
| --- | --- |
| `fasterfurnaces.admin.command` | Allows access to the admin command parent. |
| `fasterfurnaces.admin.command.give` | Allows `/fasterfurnaces admin give`. |
| `fasterfurnaces.admin.command.reload` | Allows `/fasterfurnaces admin reload`. |
| `fasterfurnaces.admin.command.list` | Allows viewing another player's furnaces with `/fasterfurnaces list [player]`. |
| `fasterfurnaces.admin.no_limits` | Assigns the default `admin` limit pack from `player-limits.yml`, removing most configured limits. |

See [Admin Commands](../admins/Commands.md) for command usage.
