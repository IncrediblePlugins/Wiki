`/lands`\
Opens the GUI menu. Executing `/lands menu` will have the same effect.\
*Permission: lands.command.menu*

`/lands help [page]`\
Display command usages of Lands.\
Permission: `lands.command.help`

`/lands claim [radius, auto, fill]`\
If no argument provided, it claims the chunk you're standing in. `radius` claims chunks in a specified radius. `auto` claims chunks while you're walking and `fill` claims all chunks that are surrounded by claimed chunks.\
Permission: `lands.command.claim`

`/lands create [newline]`\
Create a new land.\
Permission: `lands.command.create`

`/lands merge <land>`\
Merge the provided land with your current land.\
Permission: `lands.command.merge`

`/lands accept <land>`\
Accept an invitation from another land to join them.\
Permission: `lands.command.accept`

`/lands chat [land] <message>`\
Send chat messages in the land chat. If the `land` parameter is not provided, it sends a message to your current `/lands edit <land>` land.\
Permission: `lands.command.chat`

`/lands delete <land | here>`\
Delete a land or subarea at your current position. If you provide `here` for the land parameter, it will delete the subarea you're currently standin in.\
Permission: `lands.command.delete`

`/lands deny <land>`\
Deny an invitation from a land.\
Permission: `lands.command.deny`

`/lands deposit <amount> [land]`\
Deposit money to a land bank.\
Permission: `lands.command.deposit`

`/lands edit <land>`\
Enter the edit mode for a land. All following commands will be executed for this land.\
Permission: `lands.command.edit`

`/lands info [land]`\
Display information about a land. If no parameter is provided, it will display information about the land you're currently standing in.\
Permission: `lands.command.info`

`/lands invites`\
View all received invitations and ownership requests.\
Permission: `lands.command.invites`

`/lands leave <land | here>`\
Leave a land. If you provide hereˋ as the argument, you'll leave the (sub)area at your current position.\
Permission: `lands.command.leave`

`/lands map`\
View a map that shows claimed and unclaimed chunks around you. If you want to view the map in chat instead of the GUI, execute `/lands map chat`.\
Permission: `lands.command.map`

`/lands menu [menu] [additional]`\
Open the GUI menu. You can open a specific menu by providing the `[menu]` parameter. If you execute `/lands menu here`, if will open the menu for the (sub)area you're currently standing in. The `[additional]` parameter is only available for server admins to open a menu for a specific player etc.\
Permission: `lands.command.menu`

`/lands rename <new name>`\
Rename your land. Depending on the server this might charge you a fee.\
Permission: `lands.command.rename`

`/lands selection`\
Create a selection by selecting a lower and upper corner. Executing `/lands selection expand` will expand the selection to the full height. When complete, you can execute the following commands for the selection:
* `/lands claim` - claim the selection
* `/lands assign <area>` - resize an existing subarea or create a new subarea
* `/lands unclaim` - unclaim the selection\
Permission: `lands.command.selection`

`/lands assign <area>`\
Permission: `lands.command.assign`\
Assign selection to a area (resize) or create a new area. Alternatively you can use `/lands selection assign`.

`/lands setrole <player> <area,*> <role>`\
Permission: `lands.command.setrole`\
Set a role of a player.\
The area parameter defines a sub area of the land.

`/lands setspawn`\
Permission: `lands.command.setspawn`\
Set spawn for land.
      
`/lands spawn [land]`\
Permission: `lands.command.spawn`\
Teleport to land spawn.

`/lands top`\
Permission: `lands.command.top`\
Show top ten lands.

`/lands trust <player> [area,*]`\
Permission: `lands.command.trust`\
Trust a player.\
Area parameter is optional.

`/lands unclaim`\
Permission: `lands.command.unclaim`\
Unclaim a chunk.

`/lands unclaim auto`\
Permission: `lands.command.unclaim.auto`\
Unclaim chunks while walking.

`/lands unclaimall`\
Permission: `lands.command.unclaimall`\
Unclaim all chunks for the land.

`/lands untrust <player> [area,*]`\
Permission: `lands.command.untrust`\
Untrust player.\
Area parameter is optional.

`/lands storage`\
Permission: `lands.command.storage`\
Open the land item storage inventory.

`/lands view`\
Permission: `lands.command.view`\
Visualise land borders.

`/lands unstuck`\
Permission: `lands.command.unstuck`\
Teleport to the nearest unclaimed chunk. This allows you to teleport out of claims, if you're stuck inside.

`/lands wild [world] [player]`\
Permission: `lands.command.wild`\
Teleport to a random location. The optional player parameter is\
only available to players with the permission "lands.admin.command.wild"\
You can customize this command in the config file.

`/lands wild [world] [player]`\
Permission: `lands.admin.command.wild`\
Execute /wild for other players.

`/lands withdraw <amount> [land]`\
Permission: `lands.command.withdraw`\
Withdraw money from land bank.

`/lands balance [land]`\
Permission: `lands.command.balance`\
View land's balance.

`/lands taxes`\
Permission: `lands.command.taxes`\
View upcoming tax payments.

`/lands rent`\
Permission: `lands.command.rent`\
[Manage rentals.](https://lands.incredibleplugins.com/wiki/Rent-System)

`/lands relations`\
Permission: `lands.command.relations`\
Manage relations.

`/lands confirmtp`\
Permission: `None`\
Confirm unsafe destination.

### Nations
`/nations create`\
Permission: `nations.command.create`\
Create a nation.

`/nations accept`\
Permission: `nations.command.accept`\
Accept invite.

`/nations delete`\
Permission: `nations.command.delete`\
Delete nation.

`/nations deny`\
Permission: `nations.command.deny`\
Deny invite.

`/nations leave`\
Permission: `nations.command.leave`\
Leave nation.

`/nations rename`\
Permission: `nations.command.rename`\
Rename nation.

`/nations menu`\
Permission: `nations.command.menu`\
Open nation menu.

`/nations  setcapital`\
Permission: `nations.command.setcapital`\
Set capital of nation.

`/nations spawn`\
Permission: `nations.command.spawn`\
Teleport to nation spawn.

`/nations trust`\
Permission: `nations.command.trust`\
Add land.

`/nations untrust`\
Permission: `nations.command.untrust`\
Remove land.

`/nations relations`\
Permission: `nations.command.relations`\
Manage relations.

`/nations top`\
Permission: `nations.command.top`\
View top nations.

### Wars
`/wars declare`\
Permission: `wars.command.declare`\
Declare war against a land or nation.

`/wars deny`\
Permission: `wars.command.deny`\
Deny mutual war declaration.

`/wars info`\
Permission: `wars.command.info`\
Info about current war.

`/wars menu`\
Permission: `wars.command.menu`\
Open menu for current war.

`/wars list`\
Permission: `wars.command.list`\
View all active wars.

`/wars spawn`\
Permission: `wars.command.spawn`\
Teleport to the enemies border.
