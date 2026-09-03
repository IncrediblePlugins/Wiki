# Land and Nation Commands

> This page describes the latest plugin version. If these commands don't work on your server, it
> may still be running an older version.

Every land command is reached through `/lands ...` and acts on your *edit land* - the land you're
currently managing. If you're only trusted in one land, that's automatically your edit land. If
you're trusted in more than one, use `/lands edit <land>` to pick which one commands apply to.

`/land` works as well - it's the same command as `/lands`, just under an older name some players
are used to (`/land claim` and `/lands claim` are exactly the same command).

Most nation commands work the same way through `/nations ...`, acting on your edit land's nation.
`/nation` is likewise the same command as `/nations`.

War commands are not a separate command - they live under `/lands war ...` and `/nations war ...`.

Some commands only exist if your server enabled that feature. Your server may also limit commands by permission, land role, cost, cooldown, or world.

# Lands Commands

| Command | What it does |
| --- | --- |
| `/lands` | Opens the main Lands menu. |
| `/lands menu [menu] [args]` | Opens the Lands menu. Useful menu entries include `here`, `land`, `areas`, `claims`, `relations`, `map`, `inbox`, `level`, `rentable`, `all-lands`, `lands`, `nations`, and `personal-settings`. |
| `/lands help [page]` | Shows command help. |
| `/lands create [name] [tag]` | Creates a land. If you do not enter a name, Lands may ask for one in chat or in a dialog. |
| `/lands edit <land>` | Picks which of your own lands the commands below apply to. Only needed if you're trusted in more than one land. |
| `/claim` | Creates a land named after you and claims the chunk you are standing in. |
| `/lands claim` | Same command, reached from under `/lands`. With zero lands, this also auto-creates one named after you. |
| `/lands claim auto` | Toggles auto-claim while walking. |
| `/lands claim fill` | Claims empty chunks that are surrounded by your edit land. |
| `/lands claim radius <radius>` | Claims chunks around you. |
| `/lands claim list` | Shows claimed chunks for your edit land. |
| `/lands claim merge <land>` | Merges another land into your edit land. |
| `/lands unclaim` | Unclaims the chunk you are standing in, or unclaims your current selection. |
| `/unclaim` | Same command, reached as a top-level shortcut. |
| `/lands unclaim auto` | Toggles auto-unclaim while walking. |
| `/lands unclaim radius <radius>` | Unclaims chunks around you. |
| `/lands unclaim all` | Unclaims all chunks of your edit land. This requires confirmation. |
| `/lands view` | Shows nearby land borders. Make sure particles are enabled in your Minecraft settings. |
| `/view` | Same command, reached as a top-level shortcut. |
| `/lands view here` | Shows the area you are standing in. |
| `/lands view stay` | Toggles whether border particles stay at one height or follow your height. |
| `/lands view disable` | Hides border particles. |
| `/lands selection` | Turns selection mode on or off. |
| `/lands selection expand [y-min] [y-max]` | Expands your selection. Without numbers, it toggles full-height selection. |
| `/lands info player <player>` | Shows information about a player. |
| `/lands info land <land>` | Shows information about a land. |
| `/lands confirmtp` | Confirms an unsafe teleport destination. |
| `/lands rtp` | Teleports to a random location, if enabled. |
| `/lands list` | Shows lands on the server. |
| `/lands spawn [land]` | Teleports to your edit land's spawn. With `<land>`, teleports to any land's spawn instead - you can pick any land on the server, not just ones you're trusted in. |
| `/lands setspawn` | Sets your edit land's spawn. |
| `/lands unstuck` | Teleports to the nearest wilderness location if you are trapped in a claim. |
| `/lands eco taxes` | Shows upcoming taxes you may need to pay as a land member. |
| `/lands eco upkeep` | Shows upcoming upkeep for lands you own. |
| `/lands invites menu` | Shows your invites and ownership requests. |
| `/lands invites accept <land>` | Accepts a land invite or ownership request. |
| `/lands invites decline <land>` | Denies a land invite or ownership request. |
| `/lands map` | Opens the claim map. |
| `/lands rental cancel` | Cancels your rental while standing inside the rented area. |
| `/lands rental info` | Shows rent or sell information for the area you are standing in. |
| `/lands rental list` | Opens the rent and sell offers menu. |
| `/lands camp` | Opens your camp, or creates a new one if you don't have one yet, if camps are enabled. |
| `/lands chat` | Toggles land chat mode for your edit land. |
| `/lands chat <message>` | Sends a message to your edit land's chat without changing chat mode. |
| `/lands delete` | Deletes your edit land. |
| `/lands leave` | Leaves your edit land, or the area you are standing in with `here`. |
| `/lands rename <name>` | Renames your edit land. |
| `/lands member menu` | Opens member management for your edit land. |
| `/lands member trust <player>` | Trusts a player in the whole land. To trust them in only one area, use `/lands area <area> member trust <player>` instead. Also available as `/trust <player>`. |
| `/lands member untrust <player>` | Removes a player from the whole land. To remove them from only one area, use `/lands area <area> member untrust <player>` instead. Also available as `/untrust <player>`. |
| `/trust <player>` | Shortcut, same command as `/lands member trust`. |
| `/untrust <player>` | Shortcut, same command as `/lands member untrust`. |
| `/lands member setrole <player> <role>` | Sets a player's role for the whole land. To set their role in only one area, use `/lands area <area> member setrole <player> <role>` instead. |
| `/lands member setowner <player>` | Asks a member to become the new owner of your edit land. |
| `/lands member ban <player> [silent]` | Bans a player from the whole land. To ban them from only one area, use `/lands area <area> member ban <player> [silent]` instead. |
| `/lands member unban <player>` | Removes a player ban from the whole land. To unban them from only one area, use `/lands area <area> member unban <player>` instead. |
| `/lands area <name> create` | Creates a new, empty area. Use `assign` afterward (or on a land with a selection ready) to give it a shape. |
| `/lands area <area> assign` | Assigns your current selection as the area's shape, creating the area first if it doesn't exist yet. Also available as `/assign <area>`. |
| `/assign <area>` | Shortcut, same command as `/lands area <area> assign`. |
| `/lands area <area> member menu` | Opens area-scoped member management. |
| `/lands area <area> member trust/untrust/ban/unban/setrole` | Same as the land-wide member commands, scoped to one area. |
| `/lands area <area> spawn` | Teleports to the area's spawn. |
| `/lands area <area> spawn set` | Sets the area's spawn. |
| `/lands area <area> rental info` | Shows rent or sell information for the area. |
| `/lands area <area> rental remove offer` | Removes a rent or sell offer from the area. |
| `/lands area <area> rental remove tenant` | Removes the current tenant from the area. This may require compensation. |
| `/lands bank balance` | Shows your edit land's bank balance. |
| `/lands bank deposit <amount>` | Deposits money into your edit land's bank. |
| `/lands bank withdraw <amount>` | Withdraws money from your edit land's bank. |
| `/lands storage` | Opens your edit land's storage, if storage is enabled. |
| `/lands relation` | Manages your edit land's allies and enemies. |
| `/lands nation accept <nation>` | Accepts a nation invite for your edit land. |
| `/lands nation decline <nation>` | Denies a nation invite for your edit land. |
| `/lands nation leave` | Leaves your edit land's current nation. |
| `/lands nation delete` | If your edit land is the nation's capital, deletes the nation. |
| `/lands war menu` | Opens the menu for your edit land's current or upcoming war. |
| `/lands war declare <land or nation>` | Declares war, or accepts a mutual war request. |
| `/lands war info` | Shows information about the current or upcoming war. |
| `/lands war info captureflag` | Shows the capture flag recipe or capture flag information. |
| `/lands war spawn` | Teleports near the enemy side during war. |
| `/lands war koth set` | Places (or moves) your King of the Hill point during a KoTH (Player Lands) war's preparation. |
| `/lands war independence` | Declares an independence war to break free from the nation your land is a vassal of. |
| `/lands war decline` | Denies a mutual war request. |

# Nations Commands

`/nations create` and `/nations list` stay top-level. Everything about your own nation is reached
through the rest of `/nations ...`, acting on your edit land's nation.

| Command | What it does |
| --- | --- |
| `/nations create <capital> [name] [tag]` | Creates a nation with `<capital>` as the capital land. You must own that land, and it cannot already be in a nation. |
| `/nations list` | Shows nations on the server. |
| `/nations spawn [nation]` | Teleports to your own nation's capital spawn. With `<nation>`, teleports to any nation's capital spawn - you can pick any nation on the server, not just ones you're trusted in. |
| `/nations` | Opens your nation's menu, if your edit land is part of one. Otherwise shows this help listing. |
| `/nations info` | Shows information about your nation. |
| `/nations chat` | Toggles nation chat mode. |
| `/nations chat <message>` | Sends a message to nation chat without changing chat mode. |
| `/nations delete` | Deletes the nation. |
| `/nations rename <name>` | Renames the nation. |
| `/nations relation` | Manages nation allies and enemies. |
| `/nations member menu` | Opens member management. |
| `/nations member setcapital <land>` | Sets the nation's capital land. |
| `/nations member trust <land>` | Invites a land to join the nation. Also available as `/nations trust <land>`. |
| `/nations member untrust <land>` | Removes a land from the nation. Also available as `/nations untrust <land>`. |
| `/nations war menu` | Opens the menu for the nation's current or upcoming war. |
| `/nations war declare <land or nation>` | Declares war, or accepts a mutual war request. |
| `/nations war info` | Shows information about the current or upcoming war. |
| `/nations war info captureflag` | Shows the capture flag recipe or capture flag information. |
| `/nations war spawn` | Teleports near the enemy side during war. |
| `/nations war koth set` | Places (or moves) your King of the Hill point during a KoTH (Player Lands) war's preparation. |
| `/nations war decline` | Denies a mutual war request. |
