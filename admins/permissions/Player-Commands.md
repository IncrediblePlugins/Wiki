# Player Commands

This page is for server admins who assign permissions for player-facing Lands, Nations, and Wars commands.

The player-facing command explanations are in the [Player Commands](../../players/basics/Commands.md) page.

Command permissions are defined in `plugin.yml`. Some commands only exist if the matching feature is enabled in config, such as banks, taxes, upkeep, rentals, camps, relations, nations, or wars.

# Wildcards

| Permission | Gives access to |
| --- | --- |
| `lands.command.*` | All player `/lands` commands. |
| `nations.command.*` | All player `/nations` commands. |
| `wars.command.*` | All player `/wars` commands. |

# Lands Commands

| Command | Permission | Notes |
| --- | --- | --- |
| `/lands` | `lands.command.menu` | Opens the main Lands menu. |
| `/lands menu [menu] [args]` | `lands.command.menu` | Menu entry points do not have separate permission nodes. |
| `/lands help [page]` | `lands.command.help` | Shows command help. |
| `/lands create [name]` | `lands.command.create` | Feature and cost settings can still block creation. |
| `/lands createcamp [name]` | `lands.command.createcamp` | Only registered if camps are enabled. |
| `/lands claim` | `lands.command.claim` | Role flags, claim worlds, limits, costs, and claim rules still apply. |
| `/lands claim radius <radius>` | `lands.command.claim` | By default, claim subcommands inherit `lands.command.claim`. See `command.inherit-perm.claim_2`. |
| `/lands claim auto` | `lands.command.claim` | Same inheritance behavior as above. |
| `/lands claim fill` | `lands.command.claim` | Same inheritance behavior as above. |
| `/lands claimlist` | `lands.command.claimlist` | Teleporting from the claims menu also uses `lands.teleport.chunk`. |
| `/lands unclaim` | `lands.command.unclaim` | Role flags and war restrictions still apply. |
| `/lands unclaim radius <radius>` | `lands.command.unclaim` | Inherits the `/lands unclaim` permission. |
| `/lands unclaim auto` | `lands.command.unclaim` | Inherits the `/lands unclaim` permission. |
| `/lands unclaim all` | `lands.command.unclaim` | Inherits the `/lands unclaim` permission and requires confirmation. |
| `/lands unclaimall` | `lands.command.unclaimall` | Separate command for unclaiming all claims of the edit land. |
| `/lands selection` | `lands.command.selection` | Selection size is controlled by limits. |
| `/lands selection expand [y-min] [y-max]` | `lands.command.selection` | Inherits the `/lands selection` permission. |
| `/lands assign <area>` | `lands.command.assign` | Only registered if subareas are enabled. |
| `/lands selection assign <area>` | `lands.command.selection` | Same action as `/lands assign`, but as a selection subcommand. |
| `/lands delete <land or here>` | `lands.command.delete` | Deleting a land requires confirmation. |
| `/lands merge <land>` | `lands.command.merge` | Role, ownership, and cost checks still apply. |
| `/lands rename <name>` | `lands.command.rename` | Rename cost and cooldown can still apply. |
| `/lands setspawn` | `lands.command.setspawn` | Role flags and spawn costs still apply. |
| `/lands spawn [land]` | `lands.command.spawn` | Teleporting also uses `lands.teleport.land_spawn`. |
| `/lands trust <player> [area]` | `lands.command.trust` | Role flags and invite settings still apply. |
| `/lands untrust <player> [area]` | `lands.command.untrust` | Role flags still apply. |
| `/lands setrole <player> <area or *> <role>` | `lands.command.setrole` | Role priority and role flags still apply. |
| `/lands ban <player> [area] [silent]` | `lands.command.ban` | Not registered in basic mode. |
| `/lands unban <player> [area]` | `lands.command.unban` | Not registered in basic mode. |
| `/lands leave <land or here>` | `lands.command.leave` | May require confirmation if leaving removes supplied claims. |
| `/lands accept <land>` | `lands.command.accept` | Registered if invites or ownership transfer are enabled. |
| `/lands deny <land>` | `lands.command.deny` | Registered if invites or ownership transfer are enabled. |
| `/lands invites` | `lands.command.invites` | Registered if invites or ownership transfer are enabled. |
| `/lands setowner <player>` | `lands.command.setowner` | Ownership transfer settings and cost still apply. |
| `/lands relations` | `lands.command.relations` | Only registered if relations are enabled. |
| `/lands deposit <amount> [land]` | `lands.command.deposit` | Only registered if land banks are enabled. |
| `/lands withdraw <amount> [land]` | `lands.command.withdraw` | Only registered if land banks are enabled; role flag `BALANCE_WITHDRAW` still applies. |
| `/lands balance [land]` | `lands.command.balance` | Only registered if land banks are enabled. |
| `/lands taxes` | `lands.command.taxes` | Only registered if taxes are enabled. |
| `/lands upkeep` | `lands.command.upkeep` | Only registered if upkeep is enabled. |
| `/lands level` | `lands.command.level` | Only registered if land levels are enabled. |
| `/lands info [land]` | `lands.command.info` | Shows information about a land. |
| `/lands player <player>` | `lands.command.player` | Shows information about a player. |
| `/lands map` | `lands.command.map` | Map claiming still requires claim permission and normal claim checks. |
| `/lands map chat` | `lands.command.map` | Inherits the `/lands map` permission. |
| `/lands map link` | `lands.command.map` | Only available if a web map link is configured by an integration. |
| `/lands list` | `lands.command.list` | Opens the lands list. |
| `/lands top` | `lands.command.top` | Opens land leaderboard output. |
| `/lands storage` | `lands.command.storage` | Only registered if land storage is enabled. |
| `/lands view` | `lands.command.view` | Border visualization settings still apply. |
| `/lands view here` | `lands.command.view` | Inherits the `/lands view` permission. |
| `/lands view stay` | `lands.command.view` | Inherits the `/lands view` permission. |
| `/lands view disable` | `lands.command.view` | Inherits the `/lands view` permission. |
| `/lands unstuck` | `lands.command.unstuck` | Teleporting also uses `lands.teleport.unstuck`. |
| `/lands wild` | `lands.command.wild` | Teleporting also uses `lands.teleport.random_teleport`. If `random-teleport.world-perms` is enabled, players need `lands.command.wild.<world>`. |
| `/lands chat` | `lands.command.chat` | Toggles land chat mode. |
| `/lands chat [land] <message>` | `lands.command.chat` | Sends a land chat message without toggling chat mode. |
| `/lands confirmtp` | No dedicated `plugin.yml` node | Used to confirm unsafe teleport destinations. |

# Rental Commands

| Command | Permission | Notes |
| --- | --- | --- |
| `/lands rent` | `lands.command.rent` | Parent permission for rent commands. Only registered if rentals are enabled. |
| `/lands rent list` | `lands.command.rent.list` | Teleporting to rentable offers also uses `lands.teleport.rentable`. |
| `/lands rent info` | `lands.command.rent` | Inherits the parent rent permission. |
| `/lands rent cancel` | `lands.command.rent` | Inherits the parent rent permission. |
| `/lands rent remove offer` | `lands.command.rent` | Area management checks still apply. |
| `/lands rent remove tenant` | `lands.command.rent.removeTenant` | Area management checks still apply, and compensation may be required. |

# Nations Commands

| Command | Permission | Notes |
| --- | --- | --- |
| `/nations` | `nations.command.menu` | Opens the nation menu. |
| `/nations menu [nation]` | `nations.command.menu` | Opening another nation by name requires `nations.command.menu.others`. |
| `/nations create [name]` | `nations.command.create` | Nation creation settings and costs still apply. |
| `/nations delete` | `nations.command.delete` | Requires confirmation. |
| `/nations rename <name>` | `nations.command.rename` | Rename cost and cooldown can still apply. |
| `/nations setcapital` | `nations.command.setcapital` | Capital land requirements still apply. |
| `/nations trust <land>` | `nations.command.trust` | Invites a land to join the nation. |
| `/nations untrust <land>` | `nations.command.untrust` | Removes a land from the nation. |
| `/nations accept <nation>` | `nations.command.accept` | Accepts a nation invite. |
| `/nations deny <nation>` | `nations.command.deny` | Denies a nation invite. |
| `/nations leave` | `nations.command.leave` | Leaves the nation with the current edit land. |
| `/nations relations` | `nations.command.relations` | Only registered if relations are enabled. |
| `/nations spawn` | `nations.command.spawn` | Teleports to the nation capital spawn. |
| `/nations chat` | `nations.command.chat` | Toggles nation chat mode. |
| `/nations chat [nation] <message>` | `nations.command.chat` | Sends a nation chat message without toggling chat mode. |
| `/nations info [nation]` | `nations.command.info` | Shows information about a nation. |
| `/nations level` | `nations.command.level` | Only registered if nation levels are enabled. |
| `/nations menu effects` | `nations.command.menu` | Menu entry point; nation level effects must be enabled/configured. |
| `/nations menu taxes` | `nations.command.menu` | Menu entry point for nation taxes. |
| `/nations list` | `nations.command.list` | Opens the nations list. |
| `/nations top` | `nations.command.top` | Opens nation leaderboard output. |

# Wars Commands

| Command | Permission | Notes |
| --- | --- | --- |
| `/wars menu` | `wars.command.menu` | Opens the current or upcoming war menu. |
| `/wars declare <land or nation>` | `wars.command.declare` | War declaration settings still apply. |
| `/wars deny` | `wars.command.deny` | Only registered for mutual war declarations. |
| `/wars info` | `wars.command.info` | Shows information about the current or upcoming war. |
| `/wars info captureflag` | `wars.command.info.captureflag` | Shows capture flag information. |
| `/wars spawn` | `wars.command.spawn` | Teleporting also uses `lands.teleport.war`. |
| `/wars list` | `wars.command.list` | Opens the active wars list. |

# Related Teleport Permissions

These permissions are set to `true` by default in `plugin.yml`. Set them to `false` in your permission plugin if you want to block specific teleport types.

| Permission | Used by |
| --- | --- |
| `lands.teleport.chunk` | Teleporting to claimed chunks from `/lands claimlist`. |
| `lands.teleport.rentable` | Teleporting to rentable areas or areas for sale. |
| `lands.teleport.land_spawn` | Teleporting to a land spawn with `/lands spawn`. |
| `lands.teleport.random_teleport` | Random teleporting with `/lands wild`. |
| `lands.teleport.war` | Teleporting to a war spawn with `/wars spawn`. |
| `lands.teleport.sub_area` | Teleporting to a subarea from menus. |
| `lands.teleport.unstuck` | Teleporting with `/lands unstuck`. |
