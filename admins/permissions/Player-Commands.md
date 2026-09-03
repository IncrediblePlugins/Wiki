# Player Commands

This page is for server admins who assign permissions for player-facing Lands, Nations, and Wars commands.

The player-facing command explanations are in the [Player Commands](../../players/basics/Commands.md) page.

Command permissions are defined in `plugin.yml`. Some commands only exist if the matching feature is enabled in config, such as banks, taxes, upkeep, rentals, camps, subareas, relations, nations, or wars.

Every land subcommand is a direct child of `/lands` - there's no separate `/land <land> ...` tree
with a land argument anymore. `/land` is registered as a plain alias of `/lands` (same command tree,
same permission nodes) for players used to the old command name - `/land claim` is exactly the same
command as `/lands claim`, not a different one. The same applies to `/nation` as an alias of
`/nations`. There is no standalone `/wars` command; war commands live under `/lands war ...` and
`/nations war ...`. See [Command Tree Changes](Command-Tree-Changes.md) if you're upgrading from an
older version that had `/land <land> ...`/`/nation <nation> ...` with a required argument.

Since every command acts on the player's own edit land/its nation, use `/lands edit <land>` to pick
which of your own lands a command applies to when you're trusted in more than one - see
[Command Tree Changes](Command-Tree-Changes.md#lands-edit).

# Wildcards

| Permission | Gives access to |
| --- | --- |
| `lands.command.*` | All player `/lands` commands (including `/land`, `/claim`, `/trust`, `/untrust`, `/assign`). |
| `nations.command.*` | All player `/nations` commands (including `/nation`). |

# Lands Commands

| Command | Permission | Notes |
| --- | --- | --- |
| `/lands` | `lands.command.menu` | Opens the main Lands menu. |
| `/lands menu [menu] [args]` | `lands.command.menu` | Menu entry points do not have separate permission nodes. |
| `/lands help [page]` | `lands.command.help` | Shows command help. |
| `/lands create [name] [tag]` | `lands.command.create` | Feature and cost settings can still block creation. |
| `/lands edit <land>` | `lands.command.edit` | Picks which of your own lands the commands below apply to. Requires being trusted in at least two lands (or the `lands.admin.command.edit` bypass). |
| `/claim` | `lands.command.claim` | Shortcut: creates and claims a land named after the player. |
| `/lands claim` | `lands.command.claim` | Same command, reached from under `/lands`. With zero lands, auto-creates one named after you, same as `/claim`. |
| `/lands claim merge <land>` | `lands.command.claim.merge` | Merges another land into your edit land. |
| `/lands claim auto` | `lands.command.claim.auto` | Toggles auto-claim while walking. |
| `/lands claim fill` | `lands.command.claim.fill` | Claims empty chunks surrounded by your edit land. |
| `/lands claim radius <radius>` | `lands.command.claim.radius` | Claims chunks around you. |
| `/lands claim list` | `lands.command.claim.list` | Lists claimed chunks; teleporting also uses `lands.teleport.chunk`. |
| `/lands unclaim` | `lands.command.unclaim` | Same command as `/unclaim`. Role flags and war restrictions still apply. |
| `/unclaim` | `lands.command.unclaim` | Shortcut, same command as `/lands unclaim`. |
| `/lands unclaim auto` | `lands.command.unclaim.auto` | Toggles auto-unclaim while walking. |
| `/lands unclaim radius <radius>` | `lands.command.unclaim.radius` | Unclaims chunks around you. |
| `/lands unclaim all` | `lands.command.unclaim.all` | Requires confirmation. |
| `/view` | `lands.command.view` | Border visualization settings still apply. |
| `/lands view` | `lands.command.view` | Same command, reached from under `/lands`. |
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
| `/lands spawn [land] [area] [target-player] [wait]` | `lands.command.spawn` | With `<land>`, browses any land's spawn - `<land>` tab-completes every land regardless of trust or whether a spawn is set. Without it, teleports to your own edit land's spawn. Role flags and `lands.teleport.land_spawn` still apply. `target-player`/`wait` are admin-only (`lands.admin.command.edit`). |
| `/lands setspawn` | `lands.command.setspawn` | Sets your edit land's spawn (previously `/land <land> spawn set`). Role flags and spawn costs still apply. |
| `/lands unstuck` | `lands.command.unstuck` | Teleporting also uses `lands.teleport.unstuck`. |
| `/lands eco taxes` | `lands.command.eco.taxes` | Only registered if taxes are enabled. |
| `/lands eco upkeep` | `lands.command.eco.upkeep` | Only registered if upkeep is enabled. |
| `/lands invites menu` | `lands.command.invites.menu` | Registered if invites or ownership transfer are enabled. |
| `/lands invites accept <land>` | `lands.command.invites.accept` | Registered if invites or ownership transfer are enabled. |
| `/lands invites decline <land>` | `lands.command.invites.decline` | Registered if invites or ownership transfer are enabled. |
| `/lands map` | `lands.command.map` | Legacy map command. |
| `/lands rental cancel` | `lands.command.rental.cancel` | Cancels your rental as a tenant. Only registered if rentals are enabled. |
| `/lands rental info` | `lands.command.rental.info` | Only registered if rentals are enabled. |
| `/lands rental list` | `lands.command.rental.list` | Teleporting to rentable offers also uses `lands.teleport.rentable`. |
| `/lands camp` | `lands.command.camp` | Opens your camp, or creates one if you don't have one. Only registered if camps are enabled. |
| `/lands chat <message>` | `lands.command.chat` | Sends or toggles land chat for your edit land. |
| `/lands delete` | `lands.command.delete` | Requires confirmation. |
| `/lands leave` | `lands.command.leave` | May require confirmation if leaving removes supplied claims. |
| `/lands rename <name>` | `lands.command.rename` | Rename cost and cooldown can still apply. |
| `/lands member menu` | `lands.command.member.menu` | Opens member management menu for your edit land. |
| `/lands member trust <player> [duration]` | `lands.command.member.trust` | Trusts land-wide. Role flags and invite settings still apply. Use `/lands area <area> member trust <player>` to trust only in one area. Also available as `/trust`. |
| `/lands member untrust <player>` | `lands.command.member.untrust` | Removes land-wide. Role flags still apply. Use `/lands area <area> member untrust <player>` to remove from only one area. Also available as `/untrust`. |
| `/trust <player> [duration]` | `lands.command.trust` | Top-level shortcut, same command as `/lands member trust`. |
| `/untrust <player>` | `lands.command.untrust` | Top-level shortcut, same command as `/lands member untrust`. |
| `/lands member setrole <player> <role>` | `lands.command.member.setrole` | Sets the role land-wide. Role priority and role flags still apply. Use `/lands area <area> member setrole <player> <role>` to set the role in only one area. |
| `/lands member setowner <player>` | `lands.command.member.setowner` | Ownership transfer settings and cost still apply. |
| `/lands member ban <player> [silent]` | `lands.command.member.ban` | Bans land-wide. Not registered in basic mode. Use `/lands area <area> member ban <player> [silent]` to ban from only one area. |
| `/lands member unban <player>` | `lands.command.member.unban` | Unbans land-wide. Not registered in basic mode. Use `/lands area <area> member unban <player>` to unban from only one area. |
| `/lands area <area> menu` | `lands.command.area.menu` | Only registered if subareas are enabled. |
| `/lands area <name> create` | `lands.command.area.create` | Creates a new, empty area (no geometry yet). |
| `/lands area <area> assign` | `lands.command.area.assign` | Assigns your current selection as the area's geometry, auto-creating the area first if it doesn't exist yet. Also available as `/assign <area>`. Previously named `resize`. |
| `/assign <area>` | `lands.command.assign` | Top-level shortcut, same command as `/lands area <area> assign`. |
| `/lands area <area> member menu` | `lands.command.area.member.menu` | Area-scoped member management. |
| `/lands area <area> member trust/untrust/setrole/ban/unban` | `lands.command.area.member.*` | Same behavior as the land-wide member commands, scoped to one area. |
| `/lands area <area> spawn` | `lands.command.area.spawn.teleport` | Teleports to the area's spawn. |
| `/lands area <area> spawn set` | `lands.command.area.spawn.set` | Sets the area's spawn. |
| `/lands area <area> rental info` | `lands.command.area.rental.info` | Only registered if rentals are enabled. |
| `/lands area <area> rental remove offer` | `lands.command.area.rental.remove.offer` | Removes a rental/sale offer. |
| `/lands area <area> rental remove tenant` | `lands.command.area.rental.remove.tenant` | Forcefully removes the tenant; compensation may be required. |
| `/lands bank balance` | `lands.command.bank.balance` | Only registered if land banks are enabled. |
| `/lands bank deposit <amount>` | `lands.command.bank.deposit` | Only registered if land banks are enabled. |
| `/lands bank withdraw <amount>` | `lands.command.bank.withdraw` | Role flag `BALANCE_WITHDRAW` still applies. |
| `/lands storage` | `lands.command.storage` | Only registered if land storage is enabled. |
| `/lands relation` | `lands.command.relation` | Only registered if relations are enabled. |
| `/lands nation menu` | `lands.command.nation.menu` | Only registered if nations are enabled. |
| `/lands nation accept <nation>` | `lands.command.nation.accept` | Accepts a nation invite for your edit land. |
| `/lands nation decline <nation>` | `lands.command.nation.decline` | Declines a nation invite for your edit land. |
| `/lands nation leave` | `lands.command.nation.leave` | Leaves your edit land's current nation. |
| `/lands nation delete` | `lands.command.nation.delete` | Only if your edit land is the nation's capital: deletes the nation. |
| `/lands war menu` | `lands.command.war.menu` | Only registered if wars are enabled. |
| `/lands war declare <land or nation>` | `lands.command.war.declare` | War declaration settings still apply. |
| `/lands war info` | `lands.command.war.info` | Shows information about the current or upcoming war. |
| `/lands war info captureflag` | `lands.command.war.info.captureflag` | Shows capture flag information. |
| `/lands war spawn` | `lands.command.war.spawn` | Teleporting also uses `lands.teleport.war`. |
| `/lands war koth set` | `lands.command.war.koth.set` | Places (or moves) your KoTH point during a KoTH war's preparation. |
| `/lands war independence` | `lands.command.war.independence` | Declares an independence war to break free from the nation your land is a vassal of. |
| `/lands war decline` | `lands.command.war.decline` | Only registered for mutual war declarations. |

# Nation Commands

`/nations create` and `/nations list` stay top-level. Every other nation subcommand acts on your
edit land's nation.

| Command | Permission | Notes |
| --- | --- | --- |
| `/nations create <capital> [name] [tag]` | `nations.command.create` | Nation creation settings and costs still apply. |
| `/nations list` | `nations.command.list` | Opens the nations list. |
| `/nations spawn [nation]` | `nations.command.spawn` | With `<nation>`, browses any nation's capital spawn - `<nation>` tab-completes every nation regardless of trust or whether a spawn is set. Without it, teleports to your own nation's capital spawn. Role flags and `lands.teleport.land_spawn` still apply. |
| `/nations` | `nations.command.menu` | Opens your nation's menu if your edit land is in a nation; otherwise shows the help listing. |
| `/nations menu` | `nations.command.menu` | Same, explicit subcommand. |
| `/nations info` | `nations.command.info` | Shows information about your nation. |
| `/nations chat <message>` | `nations.command.chat` | Sends or toggles nation chat. |
| `/nations delete` | `nations.command.delete` | Requires confirmation. |
| `/nations rename <name>` | `nations.command.rename` | Rename cost and cooldown can still apply. |
| `/nations relation` | `nations.command.relation` | Only registered if relations are enabled. |
| `/nations member menu` | `nations.command.member.menu` | Opens member management. |
| `/nations member setcapital <land>` | `nations.command.member.setcapital` | Capital land requirements still apply. |
| `/nations member trust <land>` | `nations.command.member.trust` | Invites a land to join the nation. Also available as `/nations trust`. |
| `/nations member untrust <land>` | `nations.command.member.untrust` | Removes a land from the nation. Also available as `/nations untrust`. |
| `/nations trust <land>` | `nations.command.trust` | Shortcut, same command as `/nations member trust`. |
| `/nations untrust <land>` | `nations.command.untrust` | Shortcut, same command as `/nations member untrust`. |
| `/nations war menu` | `nations.command.war.menu` | Only registered if wars are enabled. |
| `/nations war declare <land or nation>` | `nations.command.war.declare` | War declaration settings still apply. |
| `/nations war info` | `nations.command.war.info` | Shows information about the current or upcoming war. |
| `/nations war info captureflag` | `nations.command.war.info.captureflag` | Shows capture flag information. |
| `/nations war spawn` | `nations.command.war.spawn` | Teleporting also uses `lands.teleport.war`. |
| `/nations war koth set` | `nations.command.war.koth.set` | Places (or moves) your KoTH point during a KoTH war's preparation. |
| `/nations war decline` | `nations.command.war.decline` | Only registered for mutual war declarations. |

# Related Teleport Permissions

These permissions are set to `true` by default in `plugin.yml`. Set them to `false` in your permission plugin if you want to block specific teleport types.

| Permission | Used by |
| --- | --- |
| `lands.teleport.chunk` | Teleporting to claimed chunks from `/lands claim list`. |
| `lands.teleport.rentable` | Teleporting to rentable areas or areas for sale. |
| `lands.teleport.land_spawn` | Teleporting to a land spawn with `/lands spawn`. |
| `lands.teleport.random_teleport` | Random teleporting with `/lands rtp`. |
| `lands.teleport.war` | Teleporting to a war spawn with `/lands war spawn` or `/nations war spawn`. |
| `lands.teleport.sub_area` | Teleporting to a subarea from menus. |
| `lands.teleport.unstuck` | Teleporting with `/lands unstuck`. |
