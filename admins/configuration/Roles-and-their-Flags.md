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

# Flags
## Action Flags
Actions flags represent players actions. Each flag has their own bypass and toggle permission, which is required for players to toggle the flag. The wilderness bypass permission allows a player to bypass flags set in the wilderness via `/lands admin menu`.

* **BLOCK_PLACE**\
Allows the role to place blocks.\
*Toggle permission: lands.role.setting.block_place*\
*Bypass permission: lands.bypass.block_place*\
*Wilderness bypass permission: lands.bypass.wilderness.block_place*

* **BLOCK_BREAK**\
Allows the role to break blocks.\
*Toggle permission: lands.role.setting.block_break*\
*Bypass permission: lands.bypass.block_break*\
*Wilderness bypass permission: lands.bypass.wilderness.block_break*

* **PLANT**\
Allows the role to plant crops, saplings, etc.\
*Toggle permission: lands.role.setting.plant*\
*Bypass permission: lands.bypass.plant*\
*Wilderness bypass permission: lands.bypass.wilderness.plant*

* **HARVEST**\
Allows the role to harvest crops, etc.\
*Toggle permission: lands.role.setting.harvest*\
*Bypass permission: lands.bypass.harvest*\
*Wilderness bypass permission: lands.bypass.wilderness.harvest*

* **INTERACT_GENERAL**\
Allows all types of interaction that are not covered by the other `INTERACT_<type>` flags.\
*Toggle permission: lands.role.setting.interact_general*\
*Bypass permission: lands.bypass.interact_general*\
*Wilderness bypass permission: lands.bypass.wilderness.interact_general*

* **INTERACT_CONTAINER**\
Allows the role to open containers like chests, etc.\
*Toggle permission: lands.role.setting.interact_container*\
*Bypass permission: lands.bypass.interact_container*\
*Wilderness bypass permission: lands.bypass.wilderness.interact_container*

* **INTERACT_DOOR**\
Allows the role to open and close doors.\
*Toggle permission: lands.role.setting.interact_door*\
*Bypass permission: lands.bypass.interact_door*\
*Wilderness bypass permission: lands.bypass.wilderness.interact_door*

* **INTERACT_TRAPDOOR**\
Allows the role to open and close trapdoors.\
*Toggle permission: lands.role.setting.interact_trapdoor*\
*Bypass permission: lands.bypass.interact_trapdoor*\
*Wilderness bypass permission: lands.bypass.wilderness.interact_trapdoor*
  
* **INTERACT_MECHANISM**\
Allows the role to use redstone, levers, pressure plates, etc.\
*Toggle permission: lands.role.setting.interact_mechanism*\
*Bypass permission: lands.bypass.interact_mechanism*\
*Wilderness bypass permission: lands.bypass.wilderness.interact_mechanism*

* **INTERACT_VILLAGER**\
Allows the role to interact and trade with villagers.\
*Toggle permission: lands.role.setting.interact_villager*\
*Bypass permission: lands.bypass.interact_villager*\
*Wilderness bypass permission: lands.bypass.wilderness.interact_villager*

* **BLOCK_IGNITE**\
Allows the role to ignite blocks / set blocks on fire.\
*Toggle permission: lands.role.setting.block_ignite*\
*Bypass permission: lands.bypass.block_ignite*\
*Wilderness bypass permission: lands.bypass.wilderness.block_ignite*

* **ATTACK_PLAYER**\
Should the role be able to attack players? This flag may not always take effect, if combat-tag is enabled in the config.\
*Toggle permission: lands.role.setting.attack_player*\
*Bypass permission: lands.bypass.attack_player*\
*Wilderness bypass permission: lands.bypass.wilderness.attack_player*\
  * If disabled: The role won't be able to attack anyone.
  * If enabled: The role will be able to attack other players that are also allowed to attack this role in the given claim.

* **ATTACK_ANIMAL**\
Allows the role to attack animals.\
*Toggle permission: lands.role.setting.attack_animal*\
*Bypass permission: lands.bypass.attack_animal*\
*Wilderness bypass permission: lands.bypass.wilderness.attack_animal*

* **FLY**\
Allow the role to fly within an area. Fly will be disabled if the player is not allowed to fly at a given location. If they enter a area where they're allowed to fly, Lands will automatically re-enable their fly (if fly was active before).\
This is compatible with every fly plugin.\
*Toggle permission: lands.role.setting.fly*\
*Bypass permission: lands.bypass.fly*\
*Wilderness bypass permission: lands.bypass.wilderness.fly*

* **ELYTRA**\
Allow the role to use elytras within an area.\
*Toggle permission: lands.role.setting.elytra*\
*Bypass permission: lands.bypass.elytra*\
*Wilderness bypass permission: lands.bypass.wilderness.elytra*

* **LAND_ENTER**\
Allows the role to enter a area.\
*Toggle permission: lands.role.setting.land_enter*\
*Bypass permission: lands.bypass.land_enter*\
*Wilderness bypass permission: lands.bypass.wilderness.land_enter*

* **SPAWN_TELEPORT**\
Allows the role to teleport to the land spawn.\
*Toggle permission: lands.role.setting.spawner_teleport*\
*Bypass permission: lands.bypass.spawn_teleport*\
*Wilderness bypass permission: lands.bypass.wilderness.spawn_teleport*

* **VEHICLE_USE**\
Allows the role to use or place vehicles in the area.\
*Toggle permission: lands.role.setting.vehicle_use*\
*Bypass permission: lands.bypass.vehicle_use*\
*Wilderness bypass permission: lands.bypass.wilderness.vehicle_use*

* **ITEM_PICKUP**\
Allows the role to pick up dropped items.\
*Toggle permission: lands.role.setting.item_pickup*\
*Bypass permission: lands.bypass.item_pickup*\
*Wilderness bypass permission: lands.bypass.wilderness.item_pickup*

* **ENDER_PEARL**\
Allows the role to use ender pearls.\
*Toggle permission: lands.role.setting.ender_pearl*\
*Bypass permission: lands.bypass.ender_pearl*\
*Wilderness bypass permission: lands.bypass.wilderness.enter_pearl*

* **SHEAR**\
Allows the role to shear animals.\
*Toggle permission: lands.role.setting.shear*\
*Bypass permission: lands.bypass.shear*\
*Wilderness bypass permission: lands.bypass.wilderness.shear*

* **ATTACK_MONSTER**\
Allows the role to attack monsters.
If disabled: Monsters also won't be able to damage the players of the role.\
*Toggle permission: lands.role.setting.attack_monster*\
*Bypass permission: lands.bypass.attack_monster*\
*Wilderness bypass permission: lands.bypass.wilderness.attack_monster*

* **TRAMPLE_FARMLAND**\
Allows the role to trample farmland.\
*Toggle permission: lands.role.setting.trample_farmland*\
*Bypass permission: lands.bypass.trample_farmland*\
*Wilderness bypass permission: lands.bypass.wilderness.trample_farmland*
  
* **NO_DAMAGE**\
Players of the role won't get any damage from any damage cause. This flag is hidden by default.\
*Toggle permission: lands.role.setting.no_damage*\
*Bypass permission: None*\
*Wilderness bypass permission: None*

## Management Flags
Management flags will allow players to edit flags and options for the land. Each flag has their own toggle permission, which is required for players to be able to toggle the flag. The bypass permission allows server admins to execute these management operations for other lands.

* **PLAYER_TRUST**\
Allow the role to trust other players.\
*Toggle permission: lands.role.setting.player_trust*\
*Bypass permission: lands.bypass.player_trust*

* **PLAYER_SETROLE**\
Allow the role to set roles for trusted players.
They can only edit players which have a lower role (priority) than their own.\
*Toggle permission: lands.role.setting.player_setrole*\
*Bypass permission: lands.bypass.player_setrole*

* **PLAYER_UNTRUST**\
Allow the role to untrust players.
They can only untrust players which have a lower role (priority) than their own.\
*Toggle permission: lands.role.setting.player_untrust*\
*Bypass permission: lands.bypass.player_untrust*

* **PLAYER_BAN**\
Allow the role to ban players.
They can only ban players which have a lower role (priority) than their own.\
*Toggle permission: lands.role.setting.player_ban*\
*Bypass permission: lands.bypass.player_ban*

* **SETTING_EDIT_LAND**\
Allow the role to edit natural land flags (like mob spawning etc.)\
*Toggle permission: lands.role.setting.setting_edit_land*\
*Bypass permission: lands.bypass.setting_edit_land*

* **SETTING_EDIT_ROLE**\
Allow the role to edit settings and flags of roles which have a lower priority than their own role.\
*Toggle permission: lands.role.setting.setting_edit_role*\
*Bypass permission: lands.bypass.setting_edit_role*

* **SETTING_EDIT_TAXES**\
Allow the role to edit taxes of the area. Roles with that flag won't pay taxes.
Note: It is recommended to give this permission only to trustworthy players in your land.\
*Toggle permission: lands.role.setting.setting_edit_taxes*\
*Bypass permission: lands.bypass.setting_edit_taxes*

* **SETTING_EDIT_VARIOUS**\
Allow role to set a new name for the land and to change the title.\
*Toggle permission: lands.role.setting.setting_edit_various*\
*Bypass permission: lands.bypass.setting_edit_various*

* **LAND_CLAIM**\
Allow the role to claim chunks for the land.\
*Toggle permission: lands.role.setting.land_claim*\
*Bypass permission: lands.bypass.land_claim*

* **AREA_ASSIGN**\
Create sub areas and assign a selection to a sub area (`/lands selection assign <area>`).\
*Toggle permission: lands.role.setting.area_assign*\
*Bypass permission: lands.bypass.area_assign*

* **LAND_CLAIM_BORDER**\
The players will be able to claim directly near your land, ignoring the chunk distance from config.\
*Toggle permission: lands.role.setting.land_claim_border*\
*Bypass permission: lands.bypass.land_claim_border*

* **SPAWN_SET**\
Allow the players of the role to change the spawn.\
*Toggle permission: lands.role.setting.spawn_set*\
*Bypass permission: lands.bypass.spawn_set*

* **BALANCE_WITHDRAW**\
Withdraw balance from the land bank (`/lands withdraw`).\
*Toggle permission: lands.role.setting.balance_withdraw*\
*Bypass permission: lands.bypass.balance_withdraw*

* **WAR_MANAGE**\
Declare war with your land or surrender in the war of the land.\
*Toggle permission: lands.role.setting.war_manage*\
*Bypass permission: lands.bypass.war_manage*

### Bypass Role Priority
With the permission `lands.bypass.priority` a player can bypass role priorities. That means theat they can for example untrust players with higher roles, if they have the permission to untrust any player. If they don't have this bypass permission, they won't be able to edit players with a higher role priority.
