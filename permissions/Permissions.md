To assign permissions to players you must install a permissions plugin, like [Luckperms](https://www.spigotmc.org/resources/28140). Below you find a list of permissions that you can assign to players or their permission groups. Please note that if a player has `/op`, they will have all permissions.

# Numbered Permissions
Important: 
* **Replace `<number>` with an actual number.** Example: `chestprotect.blocks.<number>` -> chestprotect.blocks.5

`uhoppers.hoppers.<number>`\
How many upgradeable hoppers can a player place? Replace `number` with an acutal number.

# Player Commands
See here: [Link](../players/Commands.md)

# Admin Commands
See here: [Link](../admins/Commands.md)

# Teleportation
The following permissions limit all teleportation initiated by UpgradeableHoppers. Players have them by default. However, in some cases
the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.

## Disabling Teleportation
If you want to disable a teleportation you need to unset the permission in your permissions plugin.
Example for LuckPerms: ``/luckperms group default permission set uhoppers.teleport.hopper false``
The value `false` is important here.

## Teleportation Permissions
`uhoppers.teleport.protection`\
Allow teleportation to hoppers through the `/hoppers list` menu. This permission is set by default.

# Bypass Permissions
`uhoppers.bypass.open`\
Open hoppers from other players.

`uhoppers.bypass.upgrade`\
Upgrade hoppers from other players.

`uhoppers.bypass.delete`\
Delete hoppers from other players.

`uhoppers.bypass.claim`\
Allow creating links in claims, in which the player is not trusted.

`uhoppers.bypass.only-land`\
Bypass `only-land` option in `config.yml` and not being able to place hoppers in lands they're trusted in.

`uhoppers.bypass.vanilla.craft`\
Bypass the option that denies crafting vanilla hoppers.

`uhoppers.bypass.vanilla.place`\
Bypass the option that denies placing vanilla hoppers.
