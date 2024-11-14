`/lands`\
Opens the GUI menu.\
Permission: `lands.command.menu`

`/lands help [page]`\
Display command usages of Lands.\
Permission: `lands.command.help`

## `/lands claim`
Claim the chunk you're standing in.\
Permission: `lands.command.claim`

### `/lands claim auto`
Claim chunks while walking.\
Permission: `lands.command.claim.auto`

### `/lands claim radius <radius>`
Claim chunks in a specific radius.\
Permission: `lands.command.claim.radius`

`/lands create`\
Create a land.\
Permission: `lands.command.create`

>`/lands merge <land>`\
Permission: `lands.command.merge`\
Merge a land (parameter) into your other land.

>`/lands accept <land>`\
Permission: `lands.command.accept`\
Accept invites.

>`/lands chat [land] <message>`\
Permission: `lands.command.chat`\
Chat with land.

>`/lands delete <land | here>`\
Permission: `lands.command.delete`\
Delete a land or subarea at your current position, if you provide "here" for the land parameter.

>`/lands deny`\
Permission: `lands.command.deny`\
Deny invite.

>`/lands deposit [land] <amount>`\
Permission: `lands.command.deposit`\
Deposit money to land bank.

>`/lands edit <land>`\
Permission: `lands.command.edit`\
Enter edit mode for a land.\
Actions like /lands claim will be executed for this land.

>`/lands info [land]`\
Permission: `lands.command.info`\
Show information about a land.

>`/lands invites`\
Permission: `lands.command.invites`\
Open received invites GUI.

>`/lands leave <land | here>`\
Permission: `lands.command.leave`\
Leave a land or the area at your current position, if you provide "here" for the land parameter.

> `/lands map`\
Permission: `lands.command.map`\
Show lands map.

>`/lands menu`\
Permission: `lands.command.menu`\
Open Lands GUI.\
Append "here" to the command to open the GUI\
for the chunk you're standing in.

>`/lands menu here`\
Permission: `lands.command.menu`\
Open Lands GUI for the chunk you're standing in.

>`/lands rename [land] <new name>`\
Permission: `lands.command.rename`\
Rename land.

> `/lands selection`\
Permission: `lands.command.selection`\
Select a region for actions like /lands claim.\
Use `/lands selection expand` to expand the selection to all y levels.\
Possible actions:\
/lands claim\
/lands unclaim\
/lands trust\
/lands untrust

>`/lands assign <area>`\
Permission: `lands.command.assign`\
Assign selection to a area (resize) or create a new area. Alternatively you can use `/lands selection assign`.

> `/lands setrole <player> <area,*> <role>`\
Permission: `lands.command.setrole`\
Set a role of a player.\
The area parameter defines a sub area of the land.

> `/lands setspawn`\
Permission: `lands.command.setspawn`\
Set spawn for land.
      
> `/lands spawn [land]`\
Permission: `lands.command.spawn`\
Teleport to land spawn.

> `/lands top`\
Permission: `lands.command.top`\
Show top ten lands.

> `/lands trust <player> [area,*]`\
Permission: `lands.command.trust`\
Trust a player.\
Area parameter is optional.

> `/lands unclaim`\
Permission: `lands.command.unclaim`\
Unclaim a chunk.

> `/lands unclaim auto`\
Permission: `lands.command.unclaim.auto`\
Unclaim chunks while walking.

> `/lands unclaimall`\
Permission: `lands.command.unclaimall`\
Unclaim all chunks for the land.

> `/lands untrust <player> [area,*]`\
Permission: `lands.command.untrust`\
Untrust player.\
Area parameter is optional.

> `/lands storage`\
Permission: `lands.command.storage`\
Open the land item storage inventory.

> `/lands view`\
Permission: `lands.command.view`\
Visualise land borders.

> `/lands unstuck`\
Permission: `lands.command.unstuck`\
Teleport to the nearest unclaimed chunk. This allows you to teleport out of claims, if you're stuck inside.

> `/lands wild [world] [player]`\
Permission: `lands.command.wild`\
Teleport to a random location. The optional player parameter is\
only available to players with the permission "lands.admin.command.wild"\
You can customize this command in the config file.

> `/lands wild [world] [player]`\
Permission: `lands.admin.command.wild`\
Execute /wild for other players.

> `/lands withdraw <amount> [land]`\
Permission: `lands.command.withdraw`\
Withdraw money from land bank.

> `/lands balance [land]`\
Permission: `lands.command.balance`\
View land's balance.

> `/lands taxes`\
Permission: `lands.command.taxes`\
View upcoming tax payments.

> `/lands rent`\
Permission: `lands.command.rent`\
[Manage rentals.](https://lands.incredibleplugins.com/wiki/Rent-System)

> `/lands relations`\
Permission: `lands.command.relations`\
Manage relations.

> `/lands confirmtp`\
Permission: `None`\
Confirm unsafe destination.

### Nations
> `/nations create`\
Permission: `nations.command.create`\
Create a nation.

> `/nations accept`\
Permission: `nations.command.accept`\
Accept invite.

> `/nations delete`\
Permission: `nations.command.delete`\
Delete nation.

> `/nations deny`\
Permission: `nations.command.deny`\
Deny invite.

> `/nations leave`\
Permission: `nations.command.leave`\
Leave nation.

> `/nations rename`\
Permission: `nations.command.rename`\
Rename nation.

> `/nations menu`\
Permission: `nations.command.menu`\
Open nation menu.

> `/nations  setcapital`\
Permission: `nations.command.setcapital`\
Set capital of nation.

> `/nations spawn`\
Permission: `nations.command.spawn`\
Teleport to nation spawn.

> `/nations trust`\
Permission: `nations.command.trust`\
Add land.

> `/nations untrust`\
Permission: `nations.command.untrust`\
Remove land.

> `/nations relations`\
Permission: `nations.command.relations`\
Manage relations.

> `/nations top`\
Permission: `nations.command.top`\
View top nations.

### Wars
> `/wars declare`\
Permission: `wars.command.declare`\
Declare war against a land or nation.

> `/wars deny`\
Permission: `wars.command.deny`\
Deny mutual war declaration.

> `/wars info`\
Permission: `wars.command.info`\
Info about current war.

> `/wars menu`\
Permission: `wars.command.menu`\
Open menu for current war.

> `/wars list`\
Permission: `wars.command.list`\
View all active wars.

> `/wars spawn`\
Permission: `wars.command.spawn`\
Teleport to the enemies border.