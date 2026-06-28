# Current Edit Land

Most land commands use your current edit land. Select it with `/lands edit <land>`.

You can also use `/lands edit` while standing inside a land you are trusted in.

If a command does not seem to affect the land you expected, check your edit land first.

Some commands only exist if your server enabled that feature. Your server may also limit commands by permission, land role, cost, cooldown, or world.

# Lands Commands

`/lands`

Open the main Lands menu.

`/lands menu [menu] [args]`

Open the Lands menu. Useful menu entries include `here`, `land`, `areas`, `claims`, `relations`, `map`, `inbox`, `level`, `rentable`, `all-lands`, `lands`, `nations`, and `personal-settings`.

`/lands help [page]`

Show command help.

`/lands create [name]`

Create a land. If you do not enter a name, Lands may ask for one in chat or in a dialog.

`/lands createcamp [name]`

Create a temporary camp, if camps are enabled.

`/lands claim`

Claim the chunk you are standing in, or claim your current selection.

`/lands claim radius <radius>`

Claim chunks around you.

`/lands claim auto`

Toggle auto-claim while walking.

`/lands claim fill`

Claim empty chunks that are surrounded by your land.

`/lands claimlist`

View claimed chunks for your land.

`/lands unclaim`

Unclaim the chunk you are standing in, or unclaim your current selection.

`/lands unclaim radius <radius>`

Unclaim chunks around you.

`/lands unclaim auto`

Toggle auto-unclaim while walking.

`/lands unclaim all`

Unclaim all chunks of your current edit land.

`/lands unclaimall`

Unclaim all chunks of your current edit land. This requires confirmation.

`/lands selection`

Turn selection mode on or off.

`/lands selection expand [y-min] [y-max]`

Expand your selection. Without numbers, it toggles full-height selection.

`/lands assign <area>`

Create or resize a subarea from your current selection.

`/lands selection assign <area>`

Same as `/lands assign <area>`.

`/lands delete <land | here>`

Delete a land, or delete the subarea you are standing in with `here`.

`/lands merge <land>`

Merge another land into your current edit land.

`/lands rename <name>`

Rename your current edit land.

`/lands setspawn`

Set your land spawn.

`/lands spawn [land]`

Teleport to a land spawn.

`/lands trust <player> [area]`

Trust a player in your whole land or in one area.

`/lands untrust <player> [area]`

Remove a player from your whole land or from one area.

`/lands setrole <player> <area | *> <role>`

Set a player's role in one area, or in all areas with `*`.

`/lands ban <player> [area] [silent]`

Ban a player from the land or an area.

`/lands unban <player> [area]`

Remove a player ban.

`/lands leave <land | here>`

Leave a land, or leave the area you are standing in with `here`.

`/lands accept <land>`

Accept a land invite or ownership request.

`/lands deny <land>`

Deny a land invite or ownership request.

`/lands invites`

View your invites and ownership requests.

`/lands setowner <player>`

Ask a member to become the new owner of your land.

`/lands relations`

Manage land allies and enemies.

`/lands deposit <amount> [land]`

Deposit money into a land bank.

`/lands withdraw <amount> [land]`

Withdraw money from a land bank.

`/lands balance [land]`

View a land bank balance.

`/lands taxes`

View upcoming taxes you may need to pay as a land member.

`/lands upkeep`

View upcoming upkeep for lands you own.

`/lands level`

View land level progress.

`/lands info [land]`

View information about a land. Without a land name, this shows the land you are standing in.

`/lands player <player>`

View information about a player.

`/lands map`

Open the claim map.

`/lands map chat`

Show the claim map in chat.

`/lands map link`

Show the web map link, if your server has one.

`/lands list`

View lands on the server.

`/lands top`

View the land leaderboard.

`/lands storage`

Open your land storage, if storage is enabled.

`/lands view`

Show nearby land borders. Make sure particles are enabled in your Minecraft settings.

`/lands view here`

Show the area you are standing in.

`/lands view stay`

Toggle whether border particles stay at one height or follow your height.

`/lands view disable`

Hide border particles.

`/lands unstuck`

Teleport to the nearest wilderness location if you are trapped in a claim.

`/lands wild`

Teleport to a random location, if enabled.

`/lands chat`

Toggle land chat mode.

`/lands chat [land] <message>`

Send a message to land chat without changing chat mode.

`/lands confirmtp`

Confirm an unsafe teleport destination.

# Rental Commands

`/lands rent list`

Open the rent and sell offers menu.

`/lands rent info`

Show rent or sell information for the area you are standing in.

`/lands rent cancel`

Cancel your rental while standing inside the rented area.

`/lands rent remove offer`

Remove a rent or sell offer from the area you are standing in.

`/lands rent remove tenant`

Remove the current tenant from the area you are standing in. This may require compensation.

# Nations Commands

`/nations`

Open your nation menu.

`/nations menu [nation]`

Open a nation menu.

`/nations create [name]`

Create a nation with your current edit land as the capital.

`/nations delete`

Delete your nation.

`/nations rename <name>`

Rename your nation.

`/nations setcapital`

Set your current edit land as the nation capital.

`/nations trust <land>`

Invite a land to join your nation.

`/nations untrust <land>`

Remove a land from your nation.

`/nations accept <nation>`

Accept a nation invite.

`/nations deny <nation>`

Deny a nation invite.

`/nations leave`

Leave the nation with your current edit land.

`/nations relations`

Manage nation allies and enemies.

`/nations spawn`

Teleport to the spawn of the nation capital.

`/nations chat`

Toggle nation chat mode.

`/nations chat [nation] <message>`

Send a message to nation chat without changing chat mode.

`/nations info [nation]`

View information about a nation.

`/nations level`

View nation level progress.

`/nations menu effects`

Open nation effects, if your server has nation level effects enabled.

`/nations menu taxes`

Open nation taxes, if your server enabled nation taxes.

`/nations list`

View nations on the server.

`/nations top`

View the nation leaderboard.

# Wars Commands

`/wars menu`

Open the menu for your current or upcoming war.

`/wars declare <land | nation>`

Declare war, or accept a mutual war request.

`/wars deny`

Deny a mutual war request.

`/wars info`

View information about your current or upcoming war.

`/wars spawn`

Teleport near the enemy side during war.

`/wars list`

View active wars.
