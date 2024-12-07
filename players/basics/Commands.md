# Current Edit Land
Most commands don't require you to provide the name of a land or nation. Commands are usually executed for the land that you selected via `/lands edit <land>`.

`/lands edit <land>`\
Enter the edit mode for a land. All following commands will be executed for this land.\
*Permission: lands.command.edit*

# Player Commands

`/lands`\
Opens the GUI menu. Executing `/lands menu` will have the same effect.\
*Permission: lands.command.menu*

`/lands menu [menu] [additional]`\
Open the GUI menu. You can open a specific menu by providing the `[menu]` parameter. If you execute `/lands menu here`, if will open the menu for the (sub)area you're currently standing in. The `[additional]` parameter is only available for server admins to open a menu for a specific player etc.\
*Permission: lands.command.menu*

`/lands help [page]`\
Display all command of Lands. Each command group has their own help command. For example `/lands claim help` will display all subcommands of the claim command.\
*Permission: lands.command.help*

`/lands create <name>`\
Create a new land. Depending on the server you might be able to use color codes and hex color.\
*Permission: lands.command.create*

`/lands createcamp <name>`\
Create a temporary land that will be deleted after a specific period. The perdiod depends on your servers configuration.\
*Permission: lands.command.createcamp*

`/lands delete <land | here>`\
Delete a land or subarea at your current position. If you provide `here` for the land parameter, it will delete the subarea you're currently standin in.\
*Permission: lands.command.delete*

`/lands selection`\
Create a selection by selecting a lower and upper corner. Executing `/lands selection expand` will expand the selection to the full height. When complete, you can execute the following commands for the selection:
* `/lands claim` - claim the selection
* `/lands assign <area>` - resize an existing subarea or create a new subarea
* `/lands unclaim` - unclaim the selection\

*Permission: lands.command.selection*

`/lands claim [radius, auto, fill]`\
If no argument provided, it claims the chunk you're standing in. `radius` claims chunks in a specified radius. `auto` claims chunks while you're walking and `fill` claims all chunks that are surrounded by claimed chunks.\
*Permission: lands.command.claim*

`/lands claimlist`\
View all claimed chunks for your land.\
*Permission: lands.command.claimlist*

`/lands unclaim`\
Unclaim the chunk you're standing in. If you created a selection via `/lands selection`, it will unclaim the selection instead. You can also execute `/lands unclaim radius` to unclaim chunks in a specific radius or `/lands unclaim auto` to unclaim chunks you're walking into. `/lands unclaim all` will unclaim all chunks for your current `/lands edit <land>` land.\
*Permission: lands.command.unclaim*

`/lands assign <area>`\
Resize an existing subarea or create a new one.\
*Permission: lands.command.assign*

`/lands merge <land>`\
Merge the provided land with your current land.\
*Permission: lands.command.merge*

`/lands relations`\
Manage relations of your land. You can add/remove allies and enemies.\
*Permission: lands.command.relations*

`/lands deposit <amount> [land]`\
Deposit money to a land bank.\
*Permission: lands.command.deposit*

`/lands withdraw <amount> [land]`\
Withdraw money from a land bank. If the `[land]` parameter isn't provided, it will withdraw money from your current land.\
*Permission: lands.command.withdraw*

`/lands balance [land]`\
View the balance of a land. If the `[land]` parameter isn't provided, it will show the balance of your current land.\
*Permission: lands.command.balance*

`/lands trust <player> [area]`\
Trust a player in the whole land or a specific (sub)area. If you don't provide a area, the player will be trusted in the whole land.\
*Permission: lands.command.trust*

`/lands untrust <player> [area]`\
Untrust a player from the whole land or a specific (sub)area. If you don't provide a area, the player will be untrusted from the whole land.\
*Permission: lands.command.untrust*

`/lands ban <player> [area] [silent]`\
Ban a player from the whole land or a specific (sub)area. If you don't provide a area, the player will be banned from the whole land. If you provide `true` for the `[silent]` argument, the player won't receive any message that they have been banned.\
*Permission: lands.command.ban*

`/lands unban <player> [area]`\
Unban a player from the whole land or a specific (sub)area. If you don't provide a area, the player will be unbanned from the whole land.\
*Permission: lands.command.unban*

`/lands setrole <player> <area | *> <role>`\
Set the role for a player in a specific area. If you provide `*` as the area name, the role will be given in all areas, if the role is available in all areas.\
*Permission: lands.command.setrole*

`/lands setowner <player>`\
Ask a land member to be the new owner of your land.\
*Permission: lands.command.setowner*

`/lands accept <land>`\
Accept an invitation from another land to join them or an ownership request.\
*Permission: lands.command.accept*

`/lands deny <land>`\
Deny an invitation from a land.\
*Permission: lands.command.deny*

`/lands level`\
View the current level progress of your land.\
*Permission: lands.command.level*

`/lands invites`\
View all received invitations and ownership requests.\
*Permission: lands.command.invites*

`/lands leave <land | here>`\
Leave a land. If you provide hereˋ as the argument, you'll leave the (sub)area at your current position.\
*Permission: lands.command.leave*

`/lands chat [land] <message>`\
Send chat messages in the land chat. If the `land` parameter is not provided, it sends a message to your current `/lands edit <land>` land.\
*Permission: lands.command.chat*

`/lands taxes`\
View upcoming tax payments that will be taken from your personal balance to stay a member in your land. This doesn't apply to lands that you own. At the time of the tax collection, you need to have enough money in your personal balance.\
*Permission: lands.command.taxes*

`/lands upkeep`\
View upcoming upkeep payments for lands that you own. These payments will, depending on your servers configuration, be taken from the land bank or personal balance. The upkeep depends on the amount of chunks your land has claimed. If your land isn't able to pay the complete upkeep and the server has land deletion enabled, the last claimed chunks may be unclaimed to compensate for the missing balance.
*Permission: lands.command.upkeep*

`/lands info [land]`\
Display information about a land. If no parameter is provided, it will display information about the land you're currently standing in.\
*Permission: lands.command.info*

`/lands player <player>`\
View information about a specific player, such as joined lands.\
*Permission: lands.command.player*

`/lands map`\
View a map that shows claimed and unclaimed chunks around you. If you want to view the map in chat instead of the GUI, execute `/lands map chat`.\
*Permission: lands.command.map*

`/lands rename <name>`\
Rename your land. Depending on the server you might be able to use color codes and hex color.\
*Permission: lands.command.rename*

`/lands setspawn`\
Set the spawn for your land.\
*Permission: lands.command.setspawn*
      
`/lands spawn [land]`\
Teleport to a land spawn. If you don't provide a land, it will teleport you to the spawn of your current `/lands edit <land>` land.\
*Permission: lands.command.spawn*

`/lands list`\
View all lands created on the server. They can be sorted by different criteria in the GUI menu.\
*Permission: lands.command.list*

`/lands storage`\
Open the virtual item storage for your land. Modifying the storage will be logged in the land inbox. So other land members will be able to see what you took or put into the storage.\
*Permission: lands.command.storage*

`/lands view`\
Visualize land borders with particles. Make sure particles aren't turned off in your Minecraft game settings.\
*Permission: lands.command.view*

`/lands unstuck`\
Teleport to the nearest unclaimed chunk. In case you're ever trapped inside claim, you can use this command to get out of it.\
*Permission: lands.command.unstuck*

`/lands wild [world] [player]`\
Teleport to a random location. The `[player]` parameter is only available to server admins and allows you to execute the command via the console for specific players.\
*Permission: lands.command.wild*
*Permission for the `[player]` parameter: lands.admin.command.wild*

`/lands rent`\
With this command you can [manage rentals](players/Rent-System.md). It allows you to cancel your current rental or remove tenants in exchange for a compensation etc.\
*Permission: lands.command.rent*

`/lands confirmtp`\
Confirm an unsafe teleport destination.\
*Permission: None*

## Nations
`/nations menu`\
Open the nation menu of your current land.\
*Permission: nations.command.menu*

`/nations create [name]`\
Create a new nation. Depending on the server you can also use color codes, including hex color.\
*Permission: nations.command.create*

`/nations delete`\
Delete the nation of your current land.\
*Permission: nations.command.delete*

`/nations rename <name>`\
Set a new name for your nation. Depending on your server you might be able to use color codes and hex color.\
*Permission: nations.command.rename*

`/nations setcapital`\
Set the capital of your nation.\
*Permission: nations.command.setcapital*

`/nations relations`\
Add/remove allies and enemies of your nation.\
*Permission: nations.command.relations*

`/nations trust <land>`\
Invite a land to join your nation.\
*Permission: nations.command.trust*

`/nations untrust <land>`\
Remove a land from your nation.\
*Permission: nations.command.untrust*

`/nations accept <nation>`\
Accept an invitation from a nation to make your land join them.\
*Permission: nations.command.accept*

`/nations deny <nation>`\
Deny an invitation from a nation.\
*Permission: nations.command.deny*

`/nations leave`\
Leave the nation of your current land.\
*Permission: nations.command.leave*

`/nations spawn`\
Teleport to the spawn of your nations capital.\
*Permission: nations.command.spawn*

`nations chat [nation] <message>`\
Send a message to all players of your nation. If the `[nation]` argument is not provided it will send a message to the nation of your current land.\
*Permission: nations.command.chat*

`/nations info [nation]`\
View information about a nation. If the `[nation]` argument isn't provided, it will show information about the nation of your current land.\
*Permission: nations.command.info*

`/nations level`\
View the level progress of your nation.\
*Permission: nations.command.level*

`/nations list`\
View all nations created on the server. They can be sorted by different criteria in the GUI meu.\
*Permission: nations.command.list*

## Wars
`/wars menu`\
Open the GUI menu for the current or upcoming war.\
*Permission: wars.command.menu*

`/wars declare <land | nation>`\
Declare war against a land or nation. If the server has mutual declarations enabled, the enemy needs to accept the war declaration before the war declaration even starts.\
*Permission: wars.command.declare*

`/wars deny`\
Deny mutual war declaration. This commands is only available if the server has mutual declarations enabled.\
*Permission: wars.command.deny*

`/wars info`\
View information about the current or upcoming war./
*Permission: wars.command.info*

`/wars spawn`\
Teleport to the entry spawn of your team during war. This will teleport you near the border of the enemy land or nation.\
*Permission: wars.command.spawn*

`/wars list`\
View all active wars on the server.\
*Permission: wars.command.list*