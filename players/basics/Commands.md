# Land and Nation Commands

> This page describes the latest plugin version. If these commands don't work on your server, it
> may still be running an older version where you select a land first with `/lands edit <land>`
> before running commands against it.

Most land commands are reached through `/land <land> ...` (also available as `/lands land <land> ...`).
`<land>` is the name of the land you want to manage - if you are trusted in more than one land, name
the one you mean.

Most nation commands work the same way through `/nation <nation> ...` (also available as
`/nations nation <nation> ...`).

War commands are not a separate command anymore - they live under `/land <land> war ...` and
`/nation <nation> war ...`.

Some commands only exist if your server enabled that feature. Your server may also limit commands by permission, land role, cost, cooldown, or world.

# Lands Commands

| Command | What it does |
| --- | --- |
| `/lands` | Opens the main Lands menu. |
| `/lands menu [menu] [args]` | Opens the Lands menu. Useful menu entries include `here`, `land`, `areas`, `claims`, `relations`, `map`, `inbox`, `level`, `rentable`, `all-lands`, `lands`, `nations`, and `personal-settings`. |
| `/lands help [page]` | Shows command help. |
| `/lands create [name] [tag]` | Creates a land. If you do not enter a name, Lands may ask for one in chat or in a dialog. |
| `/claim` | Creates a land named after you and claims the chunk you are standing in. |
| `/lands claim` | Same shortcut, reached from under `/lands`. |
| `/lands view` | Shows nearby land borders. Make sure particles are enabled in your Minecraft settings. |
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

# Land Commands

These use `/land <land> ...`, also available as `/lands land <land> ...`.

| Command | What it does |
| --- | --- |
| `/land <land>` | Opens the land's menu. |
| `/land <land> chat` | Toggles land chat mode for that land. |
| `/land <land> chat <message>` | Sends a message to that land's chat without changing chat mode. |
| `/land <land> delete` | Deletes the land. |
| `/land <land> leave` | Leaves the land, or the area you are standing in with `here`. |
| `/land <land> rename <name>` | Renames the land. |
| `/land <land> member menu` | Opens member management. |
| `/land <land> member add <player> [area]` | Trusts a player in the whole land, or in one area. |
| `/land <land> member remove <player> [area]` | Removes a player from the whole land, or from one area. |
| `/land <land> member setrole <player> <area or *> <role>` | Sets a player's role in one area, or in all areas with `*`. |
| `/land <land> member setowner <player>` | Asks a member to become the new owner of the land. |
| `/land <land> member ban <player> [area] [silent]` | Bans a player from the land or an area. |
| `/land <land> member unban <player> [area]` | Removes a player ban. |
| `/land <land> spawn` | Teleports to the land spawn. |
| `/land <land> spawn set` | Sets the land spawn. |
| `/land <land> claim` | Claims the chunk you are standing in, or claims your current selection. |
| `/land <land> claim auto` | Toggles auto-claim while walking. |
| `/land <land> claim fill` | Claims empty chunks that are surrounded by the land. |
| `/land <land> claim radius <radius>` | Claims chunks around you. |
| `/land <land> claim list` | Shows claimed chunks for the land. |
| `/land <land> claim merge <land>` | Merges another land into this one. |
| `/land <land> unclaim` | Unclaims the chunk you are standing in, or unclaims your current selection. |
| `/land <land> unclaim auto` | Toggles auto-unclaim while walking. |
| `/land <land> unclaim radius <radius>` | Unclaims chunks around you. |
| `/land <land> unclaim all` | Unclaims all chunks of the land. This requires confirmation. |
| `/land <land> area <area> resize` | Creates or resizes a subarea from your current selection. |
| `/land <land> area <area> member menu` | Opens area-scoped member management. |
| `/land <land> area <area> member add/remove/ban/unban/setrole` | Same as the land-wide member commands, scoped to one area. |
| `/land <land> area <area> rental info` | Shows rent or sell information for the area. |
| `/land <land> area <area> rental remove offer` | Removes a rent or sell offer from the area. |
| `/land <land> area <area> rental remove tenant` | Removes the current tenant from the area. This may require compensation. |
| `/land <land> bank balance` | Shows the land bank balance. |
| `/land <land> bank deposit <amount>` | Deposits money into the land bank. |
| `/land <land> bank withdraw <amount>` | Withdraws money from the land bank. |
| `/land <land> storage` | Opens the land storage, if storage is enabled. |
| `/land <land> relation` | Manages land allies and enemies. |
| `/land <land> nation accept <nation>` | Accepts a nation invite for this land. |
| `/land <land> nation decline <nation>` | Denies a nation invite for this land. |
| `/land <land> nation leave` | Leaves the land's current nation. |
| `/land <land> nation delete` | If this land is the nation's capital, deletes the nation. |
| `/land <land> war menu` | Opens the menu for the land's current or upcoming war. |
| `/land <land> war declare <land or nation>` | Declares war, or accepts a mutual war request. |
| `/land <land> war info` | Shows information about the current or upcoming war. |
| `/land <land> war info captureflag` | Shows the capture flag recipe or capture flag information. |
| `/land <land> war spawn` | Teleports near the enemy side during war. |
| `/land <land> war decline` | Denies a mutual war request. |

# Nations Commands

`/nations create` and `/nations list` stay under `/nations`. Everything about one specific nation is
reached through `/nation <nation> ...` (also available as `/nations nation <nation> ...`).

| Command | What it does |
| --- | --- |
| `/nations create <capital> [name] [tag]` | Creates a nation with `<capital>` as the capital land. You must own that land, and it cannot already be in a nation. |
| `/nations list` | Shows nations on the server. |
| `/nation <nation>` | Opens the nation menu. |
| `/nation <nation> info` | Shows information about a nation. |
| `/nation <nation> chat` | Toggles nation chat mode. |
| `/nation <nation> chat <message>` | Sends a message to nation chat without changing chat mode. |
| `/nation <nation> delete` | Deletes the nation. |
| `/nation <nation> rename <name>` | Renames the nation. |
| `/nation <nation> spawn` | Teleports to the spawn of the nation capital. |
| `/nation <nation> relation` | Manages nation allies and enemies. |
| `/nation <nation> members menu` | Opens member management. |
| `/nation <nation> members setcapital <land>` | Sets the nation's capital land. |
| `/nation <nation> members add <land>` | Invites a land to join the nation. |
| `/nation <nation> members remove <land>` | Removes a land from the nation. |
| `/nation <nation> war menu` | Opens the menu for the nation's current or upcoming war. |
| `/nation <nation> war declare <land or nation>` | Declares war, or accepts a mutual war request. |
| `/nation <nation> war info` | Shows information about the current or upcoming war. |
| `/nation <nation> war info captureflag` | Shows the capture flag recipe or capture flag information. |
| `/nation <nation> war spawn` | Teleports near the enemy side during war. |
| `/nation <nation> war decline` | Denies a mutual war request. |
