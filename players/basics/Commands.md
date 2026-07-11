# Current Edit Land

Most land commands use your current edit land. Select it with `/lands edit <land>`.

You can also use `/lands edit` while standing inside a land you are trusted in.

If a command does not seem to affect the land you expected, check your edit land first.

Some commands only exist if your server enabled that feature. Your server may also limit commands by permission, land role, cost, cooldown, or world.

# Lands Commands

| Command | What it does |
| --- | --- |
| `/lands` | Opens the main Lands menu. |
| `/lands menu [menu] [args]` | Opens the Lands menu. Useful menu entries include `here`, `land`, `areas`, `claims`, `relations`, `map`, `inbox`, `level`, `rentable`, `all-lands`, `lands`, `nations`, and `personal-settings`. |
| `/lands help [page]` | Shows command help. |
| `/lands edit [land]` | Selects the land that most land commands should use. Without a name, it selects the land you are standing in if you are trusted there. |
| `/lands create [name]` | Creates a land. If you do not enter a name, Lands may ask for one in chat or in a dialog. |
| `/lands createcamp [name]` | Creates a temporary camp, if camps are enabled. |
| `/lands claim` | Claims the chunk you are standing in, or claims your current selection. |
| `/lands claim radius <radius>` | Claims chunks around you. |
| `/lands claim auto` | Toggles auto-claim while walking. |
| `/lands claim fill` | Claims empty chunks that are surrounded by your land. |
| `/lands claimlist` | Shows claimed chunks for your land. |
| `/lands unclaim` | Unclaims the chunk you are standing in, or unclaims your current selection. |
| `/lands unclaim radius <radius>` | Unclaims chunks around you. |
| `/lands unclaim auto` | Toggles auto-unclaim while walking. |
| `/lands unclaim all` | Unclaims all chunks of your current edit land. |
| `/lands unclaimall` | Unclaims all chunks of your current edit land. This requires confirmation. |
| `/lands selection` | Turns selection mode on or off. |
| `/lands selection expand [y-min] [y-max]` | Expands your selection. Without numbers, it toggles full-height selection. |
| `/lands assign <area>` | Creates or resizes a subarea from your current selection. |
| `/lands selection assign <area>` | Same as `/lands assign <area>`. |
| `/lands delete <land or here>` | Deletes a land, or deletes the subarea you are standing in with `here`. |
| `/lands merge <land>` | Merges another land into your current edit land. |
| `/lands rename <name>` | Renames your current edit land. |
| `/lands setspawn` | Sets your land spawn. |
| `/lands spawn [land]` | Teleports to a land spawn. |
| `/lands trust <player> [area]` | Trusts a player in your whole land or in one area. |
| `/lands untrust <player> [area]` | Removes a player from your whole land or from one area. |
| `/lands setrole <player> <area or *> <role>` | Sets a player's role in one area, or in all areas with `*`. |
| `/lands ban <player> [area] [silent]` | Bans a player from the land or an area. |
| `/lands unban <player> [area]` | Removes a player ban. |
| `/lands leave <land or here>` | Leaves a land, or leaves the area you are standing in with `here`. |
| `/lands accept <land>` | Accepts a land invite or ownership request. |
| `/lands deny <land>` | Denies a land invite or ownership request. |
| `/lands invites` | Shows your invites and ownership requests. |
| `/lands setowner <player>` | Asks a member to become the new owner of your land. |
| `/lands relations` | Manages land allies and enemies. |
| `/lands deposit <amount> [land]` | Deposits money into a land bank. |
| `/lands withdraw <amount> [land]` | Withdraws money from a land bank. |
| `/lands balance [land]` | Shows a land bank balance. |
| `/lands taxes` | Shows upcoming taxes you may need to pay as a land member. |
| `/lands upkeep` | Shows upcoming upkeep for lands you own. |
| `/lands level` | Shows land level progress. |
| `/lands info [land]` | Shows information about a land. Without a land name, this shows the land you are standing in. |
| `/lands player <player>` | Shows information about a player. |
| `/lands map` | Opens the claim map. |
| `/lands map chat` | Shows the claim map in chat. |
| `/lands map link` | Shows the web map link, if your server has one. |
| `/lands list` | Shows lands on the server. |
| `/lands top` | Shows the land leaderboard. |
| `/lands storage` | Opens your land storage, if storage is enabled. |
| `/lands view` | Shows nearby land borders. Make sure particles are enabled in your Minecraft settings. |
| `/lands view here` | Shows the area you are standing in. |
| `/lands view stay` | Toggles whether border particles stay at one height or follow your height. |
| `/lands view disable` | Hides border particles. |
| `/lands unstuck` | Teleports to the nearest wilderness location if you are trapped in a claim. |
| `/lands wild` | Teleports to a random location, if enabled. |
| `/lands chat` | Toggles land chat mode. |
| `/lands chat [land] <message>` | Sends a message to land chat without changing chat mode. |
| `/lands confirmtp` | Confirms an unsafe teleport destination. |

# Rental Commands

| Command | What it does |
| --- | --- |
| `/lands rent list` | Opens the rent and sell offers menu. |
| `/lands rent info` | Shows rent or sell information for the area you are standing in. |
| `/lands rent cancel` | Cancels your rental while standing inside the rented area. |
| `/lands rent remove offer` | Removes a rent or sell offer from the area you are standing in. |
| `/lands rent remove tenant` | Removes the current tenant from the area you are standing in. This may require compensation. |

# Nations Commands

| Command | What it does |
| --- | --- |
| `/nations` | Opens your nation menu. |
| `/nations menu [nation]` | Opens a nation menu. |
| `/nations create [name]` | Creates a nation with your current edit land as the capital. |
| `/nations delete` | Deletes your nation. |
| `/nations rename <name>` | Renames your nation. |
| `/nations setcapital` | Sets your current edit land as the nation capital. |
| `/nations trust <land>` | Invites a land to join your nation. |
| `/nations untrust <land>` | Removes a land from your nation. |
| `/nations accept <nation>` | Accepts a nation invite. |
| `/nations deny <nation>` | Denies a nation invite. |
| `/nations leave` | Leaves the nation with your current edit land. |
| `/nations relations` | Manages nation allies and enemies. |
| `/nations spawn` | Teleports to the spawn of the nation capital. |
| `/nations chat` | Toggles nation chat mode. |
| `/nations chat [nation] <message>` | Sends a message to nation chat without changing chat mode. |
| `/nations info [nation]` | Shows information about a nation. |
| `/nations level` | Shows nation level progress. |
| `/nations menu effects` | Opens nation effects, if your server has nation level effects enabled. |
| `/nations menu taxes` | Opens nation taxes, if your server enabled nation taxes. |
| `/nations list` | Shows nations on the server. |
| `/nations top` | Shows the nation leaderboard. |

# Wars Commands

| Command | What it does |
| --- | --- |
| `/wars menu` | Opens the menu for your current or upcoming war. |
| `/wars declare <land or nation>` | Declares war, or accepts a mutual war request. |
| `/wars deny` | Denies a mutual war request. |
| `/wars info` | Shows information about your current or upcoming war. |
| `/wars info captureflag` | Shows the capture flag recipe or capture flag information. |
| `/wars spawn` | Teleports near the enemy side during war. |
| `/wars list` | Shows active wars. |
