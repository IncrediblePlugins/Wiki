Lands has a feature packed role system which allows each land to adjust flags for each role and create new roles for your land.
Players can change role flags by opening their land menu (`/lands`) and then navigating to the roles menu. 
You as an administrator can edit/add default roles. Wilderness flags can be edited in the `/lands admin wilderness` menu.

Whenever a new flag is added to Lands, all existing Lands will apply the flag, if specified by the flag author.              
But for future land creations, you need to configure it correctly here. Lands will always send you a popup in console and on  
admin in game accounts, if there is a new flag available.       

# Reset flag(s) to their defined state from roles.yml
`/lands admin land <land | *> resetFlag <flag | all>`\
Keep in mind that changes to the roles.yml file require a server restart or reload.
This only affects the following roles: owner, member, visitor, nation, ally

# Set flag states
`/lands admin land <land | *> setflag <flag> <state> <apply-to-visitors>`\
This also affects roles created by players. If apply-to-visitors is false, it won't set the flag for the visitor role.
             
# Add a custom role from roles.yml to a land or all existing lands
>/lands admin land <land | *> addRole <role>\
Caution: Executing this command can lead to lands having this role multiple times. For example, if an existing land already got this role assigned at land creation or if you execute this command multiple times with the same role. Since lands can change the name of a role, there is no unique identification possible by name.

# Hide / show flags from the flags menu
```yaml
  # Which flags should be displayed in the role settings menu?
  # You can still set default values below and hide them by removing them from this list.
  display:
    - BLOCK_PLACE
    - BLOCK_BREAK
    - PLANT
    - HARVEST
    - BLOCK_IGNITE
    - INTERACT_GENERAL
    - INTERACT_CONTAINER
    - INTERACT_DOOR
    - INTERACT_TRAPDOOR
    - INTERACT_MECHANISM
    - INTERACT_VILLAGER
    - ATTACK_PLAYER
    - ATTACK_ANIMAL
    - ATTACK_MONSTER
    - FLY
    - SPAWN_TELEPORT
    - ENDER_PEARL
    - LAND_ENTER
    - VEHICLE_USE
    - ITEM_PICKUP
    - TRAMPLE_FARMLAND
    - LAND_CLAIM
    - LAND_CLAIM_BORDER
    - SPAWN_SET
    - BALANCE_WITHDRAW
    - AREA_ASSIGN
    - WAR_MANAGE
    - PLAYER_TRUST
    - PLAYER_SETROLE
    - PLAYER_UNTRUST
    - PLAYER_BAN
    - SETTING_EDIT_LAND
    - SETTING_EDIT_ROLE
    - SETTING_EDIT_TAXES
    - SETTING_EDIT_VARIOUS
```

# Edit / add default Roles
You can find the configuration options in your `roles.yml` located in `/plugins/lands`. In this file you can edit existing default roles or add your own default roles. These roles will apply to new land creations.

Example Configuration of a custom default role:
````yaml
    yourCustomDefaultRole:
      name: '&eCustomDefaultRole'
      # The icon supports texture values (example: https://minecraft-heads.com/) and normal material values.
      icon: 'eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvYjFhZGZkZjA3MTE3NWFkYWQ2NDRmZTRiM2E5NzMxYWM2YThmYTQ3NTExNjJlODEzOGM4OTlmYmFhNWZmMGI5In19fQ=='
      # Default flag values. Please note that these only apply to new land creations. Players will be able to change them later in their land menu if the flag is listed under 'display' above.
      default:
        - BLOCK_PLACE
        - BLOCK_BREAK
        - INTERACT_GENERAL
        - INTERACT_DOOR
        - INTERACT_CONTAINER
        - INTERACT_MECHANISM
        - INTERACT_VILLAGER
        - BLOCK_IGNITE
        - ATTACK_PLAYER
        - ATTACK_ANIMAL
        - FLY
        - LAND_ENTER
        - SPAWN_TELEPORT
        - VEHICLE_USE
        - ITEM_PICKUP
````

# Action Flags
Actions flags represent players actions.

* **BLOCK_PLACE**\
Allows the role to place blocks.

* **BLOCK_BREAK**\
Allows the role to break blocks.

* **PLANT**\
Allows the role to plant crops, saplings, etc.

* **HARVEST**\
Allows the role to harvest crops, etc.

* **INTERACT_GENERAL**\
Allows all types of interaction that are not covered by the other `INTERACT_<type>` flags.

* **INTERACT_CONTAINER**\
Allows the role to open containers like chests, etc.

* **INTERACT_DOOR**\
Allows the role to open and close doors.

* **INTERACT_TRAPDOOR**\
Allows the role to open and close trapdoors.
  
**INTERACT_MECHANISM**\
Allows the role to use redstone, levers, pressure plates, etc.

* **INTERACT_VILLAGER**\
Allows the role to interact and trade with villagers.

* **BLOCK_IGNITE**\
Allows the role to ignite blocks / set blocks on fire.

* **ATTACK_PLAYER**\
Should the role be able to attack players? This flag may not always take effect, if combat-tag is enabled in the config.
* If disabled: The role won't be able to attack anyone.
* If enabled: The role will be able to attack other players that are also allowed to attack this role in the given claim.

* **ATTACK_ANIMAL**\
Allows the role to attack animals.

* **FLY**\
Allow the role to fly within an area. Fly will be disabled if the player is not allowed to fly at a given location. If they enter a area where they're allowed to fly, Lands will automatically re-enable their fly (if fly was active before).\
This is compatible with every fly plugin.

* **ELYTRA**\
Allow the role to use elytras within an area.

* **LAND_ENTER**\
Allows the role to enter a area.

* **SPAWN_TELEPORT**\
Allows the role to teleport to the land spawn.

* **VEHICLE_USE**\
Allows the role to use or place vehicles in the area.

* **ITEM_PICKUP**\
Allows the role to pick up dropped items.

* **ENDER_PEARL**\
Allows the role to use ender pearls.

* **SHEAR**\
Allows the role to shear animals.

* **ATTACK_MONSTER**\
Allows the role to attack monsters.
If disabled: Monsters also won't be able to damage the players of the role.

* **TRAMPLE_FARMLAND**\
Allows the role to trample farmland.
  
* **NO_DAMAGE**\
Players of the role won't get any damage from any damage cause.

# Management Flags
Management flags will allow players to edit flags and options for the land.

* **PLAYER_TRUST**\
Allow the role to trust other players.

* **PLAYER_SETROLE**\
Allow the role to set roles for trusted players.
They can only edit players which have a lower role (priority) than their own.

* **PLAYER_UNTRUST**\
Allow the role to untrust players.
They can only untrust players which have a lower role (priority) than their own.

* **PLAYER_BAN**\
Allow the role to ban players.
They can only ban players which have a lower role (priority) than their own.

* **SETTING_EDIT_LAND**\
Allow the role to edit natural land flags (like mob spawning etc.)\

* **SETTING_EDIT_ROLE**\
Allow the role to edit settings and flags of roles which have a lower priority than their own role.

* **SETTING_EDIT_TAXES**\
Allow the role to edit taxes of the area. Roles with that flag won't pay taxes.
Note: It is recommended to give this permission only to trustworthy players in your land.

* **SETTING_EDIT_VARIOUS**\
Allow role to set a new name for the land and to change the title.

* **LAND_CLAIM**\
Allow the role to claim chunks for the land.

* **AREA_ASSIGN**\
Create sub areas and assign a selection to a sub area (`/lands selection assign <area>`).

* **LAND_CLAIM_BORDER**\
The players will be able to claim directly near your land, ignoring the chunk distance from config.

* **SPAWN_SET**\
Allow the players of the role to change the spawn.

* **BALANCE_WITHDRAW**\
Withdraw balance from the land bank (`/lands withdraw`).

* **WAR_MANAGE**\
Declare war with your land or surrender in the war of the land.