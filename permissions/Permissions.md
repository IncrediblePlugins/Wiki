To assign permissions to players you must install a permissions plugin, like [Luckperms](https://www.spigotmc.org/resources/28140). Below you find a list of permissions that you can assign to players or their permission groups. Please note that if a player has `/op`, they will have all permissions.

# Recommended Permission Setup
You can find a recommended permission setup for players here: [Recommended Permission Setup](https://lands.incredibleplugins.com/wiki/Recommended-Permission-Setup)

# Player Permissions
These permissions are safe to set for your players.

## Numbered Permissions
Important: 
* **Replace `<number>` with an actual number.** Example: `lands.lands.<number>` -> lands.lands.5
* If you make changes to numbered permissions and want to synchronize these changes to lands of which the owners are offline: Execute `/lands admin land * syncPermissions`. Please note that this is not required. Without executing this command, the limits will automatically update if the land owner is online or once the land owner logs in again.

### Stacked Numbered Permissions
By default the highest numbered permission that a player has will define the limit.
You can change this by enabling the `permission-stacking` option in the `config.yml` file. This
will accumulate each limit. Example: A player has `lands.lands.5` and `lands.lands.4` set. This would result effectively in `lands.lands.9`.

### Numbered Permission Nodes
`lands.lands.<number>`\
In how many lands can the player be a member? Replace `number` with an actual number.
This does not include owned lands. If you want to set how many lands the player can own, just set the permission below (`lands.ownlands.<number>`).

`lands.ownlands.<number>`\
How many lands can the player own? Replace `number` with an acutal number.

`lands.chunks.<number>`\
How many chunks should the player be able to claim for each land they own? Replace `number` with an acutal number.

`lands.chunks.support.<number>`\
How many chunks can the player contribute to lands he's member of? Example: `lands.chunks.support.5` -> each land in which the player is trusted and not owned by the player, will receive an additional amount of 5 claims.

`lands.members.<number>`\
Set max members per land. This includes the owner. Replace `number` with an acutal number.

`lands.areas.<number>`\
Set the amount of maximum subareas for each land the player owns. Replace `number` with an acutal number.

`lands.roles.<number>`\
Set the maximum amount of roles for each land the player owns. Replace `number` with an acutal number.

`lands.rentals.<number>`\
Replace `number` with an acutal number. Allow the player to rent or buy an amount of areas per land. If set to 0, the player won't be able to rent or buy any areas. If set to 1, the player will only be able to rent or buy one area per land. And so on.

`lands.parts.<number>`\
Set the max. amount of disconnected parts for the players owned lands. This includes the initial claim. So setting `lands.parts.1`, won't do anything. This will only take effect, if the option `treat-as-new` is disabled in `config.yml`. This permission allows players to claim a collections of chunks that are disconnected from the original land, but the `force-near` option will still be enforced once the maximum amount is reached. Replace `number` with an acutal number.

`lands.free.chunks.<number>`\
The player can claim `<number>` chunks FOR FREE for each land they own. If they already claimed `<number>` of chunks this won't have any effect. Please note that an amount of chunks, depending on the "claim-radius" option in config.yml, will always be free. No matter, if this permission has been set or not.

`lands.free.lands.<number>`\
Set amount of free lands (`/lands create`). Replace `number` with an acutal number.

`lands.selection.<number>`\
The maximum amount of chunks for `/lands selection`. The default value is `1000`.

`lands.camps.<number>`\
Set the maximum amount of camps the player can create. Replace `number` with an acutal number.

`lands.allies.<number>`\
Set the maximum amount of allies per land / nation that the player owns. Replace `number` with an acutal number.

`lands.enemies.<number>`\
Set the maximum amount of enemies per land / nation that the player owns. Replace `number` with an acutal number.

`nations.lands.<number>`\
Defines how many lands can be part of each nation of that the player owns.

## Command Permissions
[Commands wiki page](players/Commands.md)

## Teleportation
The following permissions limit all teleportation initiated by Lands. Players have them by default. However, in some cases the teleportation is initiated by executing a command. In such case they need the permission to use the command as well.

### Disabling Teleportation
If you want to disable a teleportation you need to unset the permission in your permissions plugin.
Example for LuckPerms: `/luckperms group default permission set lands.teleport.sub_area false`\
The value `false` is important here.

### Teleportation Permissions
`lands.teleport.chunk`\
Allow teleportation to claimed chunks via `/lands claimlist`. This permission is set by default.

`lands.teleport.rentable`\
Allow teleportation to rentable areas or lands setup for purchase. This permission is set by default.

`lands.teleport.land_spawn`\
Allow to teleport to a land spawn. This permission is set by default.

`lands.teleport.random_teleport`\
Allow to random teleport via `/lands wild`. This permission is set by default.

`lands.teleport.war`\
Allow to teleport to war spawn via `/wars spawn`. This permission is set by default.

`lands.teleport.sub_area`\
Allow to teleport to a sub area. This permission is set by default.

`lands.teleport.unstuck`\
Allow to teleport via `/lands unstuck`. This permission is set by default.

## Toggle Natural Flags
Permissions for toggleing natural flags can be found [here](configuration/Natural-Flags.md).

## Toggle Role Flags & Bypass
Permissions for toggleing role flags can be found [here](configuration/Roles-and-their-Flags.md).

## Toggle Personal Flags
Permissions for toggleing personal flags can be found [here](configuration/Player-Personal-Settings.md).

# Staff Permissions
These permissions should only be set for your staff.

## Bypass Permissions
### WorldEdit
`lands.bypass.worldedit`\
Use worldedit in other players lands.

`lands.bypass.wilderness.worldedit`\
Use worldedit in the wilderness.

### Selection
`lands.bypass.selection`\
Bypass other plugins, such as WorldGuard, cancelling a selection creation.

### Teleport Cooldowns
`lands.bypass.cooldown.wild`\
Bypass the `/lands wild` cooldown.

`lands.bypass.cooldown.rename`\
Bypass the `/lands rename` cooldown.

`lands.bypass.cooldown.teleport`\
Bypass the chunk teleport cooldown via `/lands claimlist`.

`lands.bypass.cooldown.spawn`\
Bypass the `/lands spawn` cooldown.

`lands.bypass.cooldown.unstuck`\
Bypass the `/lands unstuck` cooldown.

### War
`lands.bypass.war.trust`\
Allow trusting other players during war.

`lands.bypass.war.claim`\
Allow claiming during war.

### Options
`lands.bypass.option.force-near`\
Bypass the `force-near` option from `config.yml`.

### Command Blacklist
`lands.bypass.cmd.untrusted.*`\
Bypass blacklisted commands for untrusted players from `config.yml`. Use `lands.bypass.cmd.untrusted.<command>` while replacing `<command>` with a command to bypass the restriction for a specific command.

`lands.bypass.cmd.general.*`\
Bypass blacklisted commands for untrusted **and trusted** players from `config.yml`. Use `lands.bypass.cmd.general.<command>` while replacing `<command>` with a command to bypass the restriction for a specific command.

```yaml
          lands.bypass.worldedit:
            description: Bypass WorldEdit restrictions in other players lands
          lands.bypass.selection:
            description: Bypass error message of other plugin cancelling selection
            
          lands.bypass.wilderness.*:
            description: Bypass all wilderness protections (for worlds in disallow-wilderness_list)
            children:
              lands.bypass.wilderness.worldedit:
                description: Bypass WorldEdit restrictions in wilderness.

          lands.bypass.cooldown.*:
            description: Bypass cooldowns
            children:
              lands.bypass.cooldown.wild:
                description: Bypass /lands wild cooldown
              lands.bypass.cooldown.rename:
                description: Bypass /lands rename cooldown
              lands.bypass.cooldown.teleport:
                description: Bypass chunk teleport cooldown
              lands.bypass.cooldown.spawn:
                description: Bypass /lands spawn cooldown
              lands.bypass.cooldown.unstuck:
                description: Bypass /lands unstuck cooldown

          lands.bypass.war.*:
            description: Bypass war restrictions
            children:
              lands.bypass.war.trust:
                description: Trust players during war.
              lands.bypass.war.claim:
                description: Claim during war.

          lands.bypass.option.*:
            description: Bypass special config options.
            children:
              lands.bypass.option.force-near:
                description: Bypass force-near option from config.

          lands.bypass.cmd.untrusted.*:
            description: Bypass blacklisted commands for untrusted players from config.yml. Use lands.bypass.cmd.untrusted.COMMAND to specify a command.
          lands.bypass.cmd.general.*:
            description: Bypass blacklisted commands for untrusted and trusted players from config.yml. Use lands.bypass.cmd.general.COMMAND to specify a command.
          lands.bypass.priority:
            description: Edit roles even if they have the same or a higher priority than your own role.
          lands.bypass.expiration:
            description: This permission only works when you use Luckperms as your permission plugin. Players with this permission will bypass the configured land expiration from your config.

          lands.bypass.teleport.*:
            description: Bypass teleport restrictions.
            children:
              lands.bypass.teleport.delay:
                description: Skip teleport delay.
              lands.bypass.teleport.cmd:
                description: Execute commands during teleportation.
```

## Admin & Moderator Utilities
See [here](admins/Admin-Tools.md).

# Administrator Permissions
Permissions for toggleing role flags can be found [here](admins/Commands.md).
