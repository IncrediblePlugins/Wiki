# Permissions

Use a permissions plugin such as [LuckPerms](https://www.spigotmc.org/resources/28140) to assign
permissions to players and groups.

Players with `/op` usually have all permissions.

# Player Command Permissions

See [Commands](../players/Commands.md) for the command list.

| Permission | What it allows |
| --- | --- |
| `chestprotect.command.menu` | Open the main menu. |
| `chestprotect.command.lock` | Use lock mode. |
| `chestprotect.command.unlock` | Use unlock mode. |
| `chestprotect.command.trust` | Use trust mode. |
| `chestprotect.command.untrust` | Use untrust mode. |
| `chestprotect.command.view` | Visualize nearby protections. |
| `chestprotect.command.exit` | Exit the active click mode. |
| `chestprotect.command.help` | View command help. |
| `chestprotect.command.*` | All player command permissions. |

# Admin-Aware Player Commands

| Permission | What it allows |
| --- | --- |
| `chestprotect.admin.lock` | Use `/chestprotect lock <player>` or `/chestprotect lock Server` to create a protection owned by another player or the server owner ID. |

# Limit Permissions

See [Limits](../config/Limits.md) for limit configuration details.

Replace `<number>` with an actual number.

| Permission | What it sets |
| --- | --- |
| `chestprotect.blocks.<number>` | Block protection limit. |
| `chestprotect.entities.<number>` | Entity protection limit. |
| `chestprotect.groups.<number>` | Group limit. |
| `chestprotect.members.<number>` | Trusted members per protection or group. |
| `chestprotect.free.blocks.<number>` | Free block protections, and currently free entity protections in the plugin build. |

# Setting Toggle Permissions

| Permission | What it allows |
| --- | --- |
| `chestprotect.setting.open` | Toggle the `OPEN` role flag. |
| `chestprotect.setting.hopper_transfer` | Toggle the `HOPPER_TRANSFER` role flag. |
| `chestprotect.setting.player_trust` | Toggle the `PLAYER_TRUST` role flag. |
| `chestprotect.setting.player_untrust` | Toggle the `PLAYER_UNTRUST` role flag. |
| `chestprotect.setting.player_setrole` | Toggle the `PLAYER_SETROLE` role flag. |
| `chestprotect.setting.unlock` | Toggle the `UNLOCK` role flag. |
| `chestprotect.setting.edit_flags` | Toggle the `EDIT_FLAGS` role flag. |
| `chestprotect.setting.player.auto_lock` | Toggle auto lock. |
| `chestprotect.setting.player.persistent_lock` | Toggle persistent lock and unlock mode. |
| `chestprotect.setting.player.persistent_trust` | Toggle persistent trust and untrust mode. |
| `chestprotect.setting.player.notifications` | Toggle opening notifications. |
| `chestprotect.setting.*` | All setting permissions. |

# Teleportation

`chestprotect.teleport.protection` allows teleportation to protections from the menu. It is set by
default.

To disable it with LuckPerms:

```text
/luckperms group default permission set chestprotect.teleport.protection false
```

The `false` value is important.

# Admin Permissions

See [Admin Commands](../admins/Commands.md) for command-specific admin permissions.

| Permission | What it allows |
| --- | --- |
| `chestprotect.admin.command` | Use `/chestprotect admin`. |
| `chestprotect.admin.command.*` | Use all admin commands. |
| `chestprotect.admin.edit` | Edit other players' protections in menus. |
| `chestprotect.admin.priority` | Bypass role priority restrictions. |
| `chestprotect.admin.lock` | Lock objects for another player or for the server owner ID. |
| `chestprotect.admin.*` | All admin permissions. |

# Bypass Permissions

Bypass permissions should only be given to staff or trusted admin groups.

| Permission | What it bypasses |
| --- | --- |
| `chestprotect.bypass.open` | Open other players' protections. |
| `chestprotect.bypass.hopper_transfer` | Hopper transfer role checks. |
| `chestprotect.bypass.player_trust` | Trust role checks. |
| `chestprotect.bypass.player_untrust` | Untrust role checks. |
| `chestprotect.bypass.player_setrole` | Role-change checks. |
| `chestprotect.bypass.unlock` | Unlock other players' protections. |
| `chestprotect.bypass.edit_flags` | Edit-flag checks. |
| `chestprotect.bypass.untrust` | Command-mode untrust bypass check. |
| `chestprotect.bypass.*` | All bypass permissions. |
