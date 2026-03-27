## Numbered Permissions
Warning: For new servers we highly recommend using the new player-limits.yml file instead: [Link](https://wiki.incredibleplugins.com/general/locale-and-config/limits)

Important:
* **Replace `<number>` with an actual number.** Example: `lands.lands.<number>` -> lands.lands.5
* If you make changes to numbered permissions and want to synchronize these changes to lands of which the owners are offline: Execute `/lands admin land * syncPermissions`. Please note that this is not required. Without executing this command, the limits will automatically update if the land owner is online or once the land owner logs in again.

### Numbered Permission Nodes
`lands.lands.<number>`\
In how many lands can the player be a member? Replace `number` with an actual number.
This does not include owned lands. If you want to set how many lands the player can own, just set the permission below (`lands.ownlands.<number>`).

`lands.ownlands.<number>`\
How many lands can the player own? Replace `number` with an actual number.

`lands.chunks.<number>`\
How many chunks should the player be able to claim for each land they own? Replace `number` with an actual number.

`lands.chunks.support.<number>`\
How many chunks can the player contribute to lands he's member of? Example: `lands.chunks.support.5` -> each land in which the player is trusted and not owned by the player, will receive an additional amount of 5 claims.

`lands.members.<number>`\
Set max members per land. This includes the owner. Replace `number` with an actual number.

`lands.areas.<number>`\
Set the amount of maximum subareas for each land the player owns. Replace `number` with an actual number.

`lands.roles.<number>`\
Set the maximum amount of roles for each land the player owns. Replace `number` with an actual number.

`lands.rentals.<number>`\
Replace `number` with an actual number. Allow the player to rent or buy an amount of areas per land. If set to 0, the player won't be able to rent or buy any areas. If set to 1, the player will only be able to rent or buy one area per land. And so on.

`lands.parts.<number>`\
Set the max. amount of disconnected parts for the players owned lands. This includes the initial claim. So setting `lands.parts.1`, won't do anything. This will only take effect, if the option `treat-as-new` is disabled in `config.yml`. This permission allows players to claim a collections of chunks that are disconnected from the original land, but the `force-near` option will still be enforced once the maximum amount is reached. Replace `number` with an actual number.

`lands.free.chunks.<number>`\
The player can claim `<number>` chunks FOR FREE for each land they own. If they already claimed `<number>` of chunks this won't have any effect. Please note that an amount of chunks, depending on the "claim-radius" option in config.yml, will always be free. No matter, if this permission has been set or not.

`lands.free.lands.<number>`\
Set amount of free lands (`/lands create`). Replace `number` with an actual number.

`lands.selection.<number>`\
The maximum amount of chunks for `/lands selection`. The default value is `1000`.

`lands.camps.<number>`\
Set the maximum amount of camps the player can create. Replace `number` with an actual number.

`lands.allies.<number>`\
Set the maximum amount of allies per land / nation that the player owns. Replace `number` with an actual number.

`lands.enemies.<number>`\
Set the maximum amount of enemies per land / nation that the player owns. Replace `number` with an actual number.

`nations.lands.<number>`\
Defines how many lands can be part of each nation of that the player owns.
