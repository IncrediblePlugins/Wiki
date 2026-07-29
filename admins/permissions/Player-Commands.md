# Player Commands

This page is for server admins who assign permissions for player-facing Lands, Nations, and Wars commands.

The player-facing command explanations are in the [Player Commands](../../players/basics/Commands.md) page.

Command permissions are defined in `plugin.yml`. Some commands only exist if the matching feature is enabled in config, such as banks, taxes, upkeep, rentals, camps, subareas, relations, nations, or wars.

Land commands are reachable both as `/land <land> ...` and as `/lands land <land> ...` - they are
the exact same command, just registered under two entry points. The same applies to
`/nation <nation> ...` and `/nations nation <nation> ...`. There is no standalone `/wars` command;
war commands live under `/land <land> war ...` and `/nation <nation> war ...`.

# Wildcards

| Permission | Gives access to |
| --- | --- |
| `lands.command.*` | All player `/lands` commands (including `/land` and `/claim`). |
| `nations.command.*` | All player `/nations` commands (including `/nation`). |

# Lands Commands

| Command | Permission | Notes |
| --- | --- | --- |
| `/lands` | `lands.command.menu` | Opens the main Lands menu. |
| `/lands menu [menu] [args]` | `lands.command.menu` | Menu entry points do not have separate permission nodes. |
| `/lands help [page]` | `lands.command.help` | Shows command help. |
| `/lands create [name] [tag]` | `lands.command.create` | Feature and cost settings can still block creation. |
| `/claim` | `lands.command.claim` | Shortcut: creates and claims a land named after the player. |
| `/lands claim` | `lands.command.claim` | Same shortcut, reached from under `/lands`. |
| `/lands view` | `lands.command.view` | Border visualization settings still apply. |
| `/lands view here` | `lands.command.view` | Inherits the `/lands view` permission. |
| `/lands view stay` | `lands.command.view` | Inherits the `/lands view` permission. |
| `/lands view disable` | `lands.command.view` | Inherits the `/lands view` permission. |
| `/lands selection` | `lands.command.selection` | Selection size is controlled by limits. |
| `/lands selection expand [y-min] [y-max]` | `lands.command.selection` | Inherits the `/lands selection` permission. |
| `/lands info player <player>` | `lands.command.info.player` | Shows information about a player. |
| `/lands info land <land>` | `lands.command.info.land` | Shows information about a land. |
| `/lands confirmtp` | `lands.command.confirmtp` | Confirms unsafe teleport destinations. |
| `/lands rtp` | `lands.command.rtp` | Random teleport. Teleporting also uses `lands.teleport.random_teleport`. |
| `/lands list` | `lands.command.list` | Opens the lands list. |
| `/lands unstuck` | `lands.command.unstuck` | Teleporting also uses `lands.teleport.unstuck`. |
| `/lands eco taxes` | `lands.command.eco.taxes` | Only registered if taxes are enabled. |
| `/lands eco upkeep` | `lands.command.eco.upkeep` | Only registered if upkeep is enabled. |
| `/lands invites menu` | `lands.command.invites.menu` | Registered if invites or ownership transfer are enabled. |
| `/lands invites accept <land>` | `lands.command.invites.accept` | Registered if invites or ownership transfer are enabled. |
| `/lands invites decline <land>` | `lands.command.invites.decline` | Registered if invites or ownership transfer are enabled. |
| `/lands map` | `lands.command.map` | Legacy map command. |
| `/lands rental cancel` | `lands.command.rental.cancel` | Only registered if rentals are enabled. |
| `/lands rental info` | `lands.command.rental.info` | Only registered if rentals are enabled. |
| `/lands rental list` | `lands.command.rental.list` | Teleporting to rentable offers also uses `lands.teleport.rentable`. |

# Land Commands

These are reached through `/land <land> ...` or `/lands land <land> ...`.

| Command | Permission | Notes |
| --- | --- | --- |
| `/land <land>` | `lands.command.land` | Opens the land's menu. |
| `/land <land> menu` | `lands.command.land.menu` | Same as above, explicit subcommand. |
| `/land <land> chat <message>` | `lands.command.land.chat` | Sends or toggles land chat. |
| `/land <land> delete` | `lands.command.land.delete` | Requires confirmation. |
| `/land <land> leave` | `lands.command.land.leave` | May require confirmation if leaving removes supplied claims. |
| `/land <land> rename <name>` | `lands.command.land.rename` | Rename cost and cooldown can still apply. |
| `/land <land> member menu` | `lands.command.land.member.menu` | Opens member management menu. |
| `/land <land> member add <player>` | `lands.command.land.member.add` | Trusts land-wide. Role flags and invite settings still apply. Use `/land <land> area <area> member add <player>` to trust only in one area. |
| `/land <land> member remove <player>` | `lands.command.land.member.remove` | Removes land-wide. Role flags still apply. Use `/land <land> area <area> member remove <player>` to remove from only one area. |
| `/land <land> member setrole <player> <role>` | `lands.command.land.member.setrole` | Sets the role land-wide. Role priority and role flags still apply. Use `/land <land> area <area> member setrole <player> <role>` to set the role in only one area. |
| `/land <land> member setowner <player>` | `lands.command.land.member.setowner` | Ownership transfer settings and cost still apply. |
| `/land <land> member ban <player> [silent]` | `lands.command.land.member.ban` | Bans land-wide. Not registered in basic mode. Use `/land <land> area <area> member ban <player> [silent]` to ban from only one area. |
| `/land <land> member unban <player>` | `lands.command.land.member.unban` | Unbans land-wide. Not registered in basic mode. Use `/land <land> area <area> member unban <player>` to unban from only one area. |
| `/land <land> spawn` | `lands.command.land.spawn.teleport` | Teleporting also uses `lands.teleport.land_spawn`. |
| `/land <land> spawn set` | `lands.command.land.spawn.set` | Role flags and spawn costs still apply. |
| `/land <land> claim` | `lands.command.land.claim` | Role flags, claim worlds, limits, costs, and claim rules still apply. |
| `/land <land> claim auto` | `lands.command.land.claim.auto` | Inherits claim checks. |
| `/land <land> claim fill` | `lands.command.land.claim.fill` | Inherits claim checks. |
| `/land <land> claim radius <radius>` | `lands.command.land.claim.radius` | Inherits claim checks. |
| `/land <land> claim list` | `lands.command.land.claim.list` | Lists claimed chunks; teleporting also uses `lands.teleport.chunk`. |
| `/land <land> claim merge <land>` | `lands.command.land.claim.merge` | Role, ownership, and cost checks still apply. |
| `/land <land> unclaim` | `lands.command.land.unclaim` | Role flags and war restrictions still apply. |
| `/land <land> unclaim auto` | `lands.command.land.unclaim.auto` | Inherits unclaim checks. |
| `/land <land> unclaim radius <radius>` | `lands.command.land.unclaim.radius` | Inherits unclaim checks. |
| `/land <land> unclaim all` | `lands.command.land.unclaim.all` | Requires confirmation. |
| `/land <land> area menu` | `lands.command.land.area.menu` | Only registered if subareas are enabled. |
| `/land <land> area <area> resize` | `lands.command.land.area.resize` | Resizes the area to the current selection. |
| `/land <land> area <area> member menu` | `lands.command.land.area.member.menu` | Area-scoped member management. |
| `/land <land> area <area> member add/remove/ban/unban/setrole` | `lands.command.land.area.member.*` | Same behavior as the land-wide member commands, scoped to one area. |
| `/land <land> area <area> rental info` | `lands.command.land.area.rental.info` | Only registered if rentals are enabled. |
| `/land <land> area <area> rental remove offer` | `lands.command.land.area.rental.remove.offer` | Removes a rental/sale offer. |
| `/land <land> area <area> rental remove tenant` | `lands.command.land.area.rental.remove.tenant` | Forcefully removes the tenant; compensation may be required. |
| `/land <land> bank balance` | `lands.command.land.bank.balance` | Only registered if land banks are enabled. |
| `/land <land> bank deposit <amount>` | `lands.command.land.bank.deposit` | Only registered if land banks are enabled. |
| `/land <land> bank withdraw <amount>` | `lands.command.land.bank.withdraw` | Role flag `BALANCE_WITHDRAW` still applies. |
| `/land <land> storage` | `lands.command.land.storage` | Only registered if land storage is enabled. |
| `/land <land> relation` | `lands.command.land.relation` | Only registered if relations are enabled. |
| `/land <land> nation menu` | `lands.command.land.nation.menu` | Only registered if nations are enabled. |
| `/land <land> nation accept <nation>` | `lands.command.land.nation.accept` | Accepts a nation invite for this land. |
| `/land <land> nation decline <nation>` | `lands.command.land.nation.decline` | Declines a nation invite for this land. |
| `/land <land> nation leave` | `lands.command.land.nation.leave` | Leaves the land's current nation. |
| `/land <land> nation delete` | `lands.command.land.nation.delete` | Only if this land is the nation's capital: deletes the nation. |
| `/land <land> war menu` | `lands.command.land.war.menu` | Only registered if wars are enabled. |
| `/land <land> war declare <land or nation>` | `lands.command.land.war.declare` | War declaration settings still apply. |
| `/land <land> war info` | `lands.command.land.war.info` | Shows information about the current or upcoming war. |
| `/land <land> war info captureflag` | `lands.command.land.war.info.captureflag` | Shows capture flag information. |
| `/land <land> war spawn` | `lands.command.land.war.spawn` | Teleporting also uses `lands.teleport.war`. |
| `/land <land> war decline` | `lands.command.land.war.decline` | Only registered for mutual war declarations. |

# Nation Commands

`/nations create` and `/nations list` stay under `/nations`. Everything about one specific nation is
reached through `/nation <nation> ...` or `/nations nation <nation> ...`.

| Command | Permission | Notes |
| --- | --- | --- |
| `/nations create <capital> [name] [tag]` | `nations.command.create` | Nation creation settings and costs still apply. |
| `/nations list` | `nations.command.list` | Opens the nations list. |
| `/nation <nation>` | `nations.command.nation` | Opens the nation menu. |
| `/nation <nation> menu` | `nations.command.nation.menu` | Same, explicit subcommand. |
| `/nation <nation> info` | `nations.command.nation.info` | Shows information about a nation. |
| `/nation <nation> chat <message>` | `nations.command.nation.chat` | Sends or toggles nation chat. |
| `/nation <nation> delete` | `nations.command.nation.delete` | Requires confirmation. |
| `/nation <nation> rename <name>` | `nations.command.nation.rename` | Rename cost and cooldown can still apply. |
| `/nation <nation> spawn` | `nations.command.nation.spawn` | Teleports to the nation capital spawn. |
| `/nation <nation> relation` | `nations.command.nation.relation` | Only registered if relations are enabled. |
| `/nation <nation> members menu` | `nations.command.nation.members.menu` | Opens member management. |
| `/nation <nation> members setcapital <land>` | `nations.command.nation.members.setcapital` | Capital land requirements still apply. |
| `/nation <nation> members add <land>` | `nations.command.nation.members.add` | Invites a land to join the nation. |
| `/nation <nation> members remove <land>` | `nations.command.nation.members.remove` | Removes a land from the nation. |
| `/nation <nation> war menu` | `nations.command.nation.war.menu` | Only registered if wars are enabled. |
| `/nation <nation> war declare <land or nation>` | `nations.command.nation.war.declare` | War declaration settings still apply. |
| `/nation <nation> war info` | `nations.command.nation.war.info` | Shows information about the current or upcoming war. |
| `/nation <nation> war info captureflag` | `nations.command.nation.war.info.captureflag` | Shows capture flag information. |
| `/nation <nation> war spawn` | `nations.command.nation.war.spawn` | Teleporting also uses `lands.teleport.war`. |
| `/nation <nation> war decline` | `nations.command.nation.war.decline` | Only registered for mutual war declarations. |

# Related Teleport Permissions

These permissions are set to `true` by default in `plugin.yml`. Set them to `false` in your permission plugin if you want to block specific teleport types.

| Permission | Used by |
| --- | --- |
| `lands.teleport.chunk` | Teleporting to claimed chunks from `/land <land> claim list`. |
| `lands.teleport.rentable` | Teleporting to rentable areas or areas for sale. |
| `lands.teleport.land_spawn` | Teleporting to a land spawn with `/land <land> spawn`. |
| `lands.teleport.random_teleport` | Random teleporting with `/lands rtp`. |
| `lands.teleport.war` | Teleporting to a war spawn with `/land <land> war spawn` or `/nation <nation> war spawn`. |
| `lands.teleport.sub_area` | Teleporting to a subarea from menus. |
| `lands.teleport.unstuck` | Teleporting with `/lands unstuck`. |
