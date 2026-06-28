# Admin and Moderation Tools

These tools are for server staff.

# Edit Other Lands

`/lands edit <land>` selects a land for admin editing. Many normal player commands then run against that selected land.

Permission:

`lands.admin.command.edit`

# Open Another Player's Menu

`/lands menu <player>` opens the Lands menu view for a player.

Permission:

`lands.admin.command.menu`

# Chat Spy

`/lands admin chatspy <land or nation or *>` toggles chat spy for one land, one nation, or all lands and nations.

Run `/lands admin chatspy` without an argument to disable all selected chat spy targets.

Permission:

`lands.admin.command.chatspy`

# Teleport Other Players

Random teleport another player:

`/lands wild <world> <player> [skip-cooldown]`

Permission:

`lands.admin.command.wild`

Teleport another player to a spawn:

`/lands spawn <land or none> <area or none> <player> <wait>`

Use `none` for the land to use the player's current edit land. Use `none` for the area to use the land spawn instead of a sub-area spawn.

Permission:

`lands.admin.command.edit`

# Leaderboard Holograms

| Command | Permission |
| --- | --- |
| `/lands admin hologram create <context> <sorting>` | `lands.admin.command.hologram.create` |
| `/lands admin hologram list` | `lands.admin.command.hologram.list` |
| `/lands admin hologram delete` | `lands.admin.command.hologram.delete` |

A supported hologram provider must be installed.

# Permission Debugging

`/lands admin listperms <player>` lists permissions detected for a player.

Permission:

`lands.admin.command.listperms`

This is useful when a wildcard or inherited group gives a player access that is hard to spot.
