## Numbered Permissions
IMPORTANT: **Replace `<number>` with an actual number.** Example: `chestprotect.blocks.<number>` -> chestprotect.blocks.50

`chestprotect.blocks.<number>`\
Description: How many blocks can a player protect?

`chestprotect.entities.<number>`\
Description: How many entities can a player protect?

`chestprotect.members.<number>`\
Description: How many trusted players can\
a player have per protection.

`chestprotect.groups.<number>`\
Description: How many groups can a player create?

`chestprotect.free.blocks.<number>`\
Description: Set free block protections amount.

`chestprotect.free.entities.<number>`\
Description: Set free entity protections amount.

## Command Permissions
See here: [Link](../players/Commands.md)

## Teleportation
The following permissions limit all teleportation initiated by ChestProtect. Players have them by default. However, in some cases
the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.
You don't need to explicitly set them.

### Disabling Teleportation
If you want to disable a teleportation you
need to unset the permission in your permissions plugin.
Example for LuckPerms: ``/luckperms group default permission set chestprotect.teleport.protection false``
The value ``false`` is important here.

### Teleportation Permissions
`chestprotect.teleport.protection`\
Description: Allow teleportation to protections.\
Note: This permission is set by default.

## Settings Permissions

      chestprotect.setting.*:
        description: Access to all protection and player settings
        default: op
        children:
          chestprotect.setting.player.*:
            description: Access to all player settings
            default: op
            children:
              chestprotect.setting.player.lock_persistent:
                description: Access to toggle lock persistent setting
                default: op
              chestprotect.setting.player.unlock_persistent:
                description: Access to toggle unlock persistent setting
                default: op
              chestprotect.setting.player.trust_persistent:
                description: Access to toggle trust persistent setting
                default: op
              chestprotect.setting.player.untrust_persistent:
                description: Access to toggle untrust persistent setting
                default: op
              chestprotect.setting.player.setrole_persistent:
                description: Access to toggle setrole persistent setting
                default: op
          chestprotect.setting.protection.*:
            description: Access to all protection settings
            default: op
            children:
              chestprotect.setting.protection.player_trust:
                description: Access to toggle role player trust setting
                default: op
              chestprotect.setting.protection.player_untrust:
                description: Access to toggle role player untrust setting
                default: op
              chestprotect.setting.protection.player_setrole:
                description: Access to toggle role player setrole setting
                default: op


## Bypass Permissions

      chestprotect.bypass.*:
        description: Bypass all protections
        default: op
        children:
          chestprotect.bypass.edit:
            description: Edit other players protections
            default: op
          chestprotect.bypass.open:
            description: Open other players protections
            default: op
          chestprotect.bypass.unlock:
            description: Unlock other players protections
            default: op


## Admin Command Permissions
See here: [Link](../admins/Commands.md
)