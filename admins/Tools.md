# Admin and Moderation Tools

These tools are for server staff.

# Manage Other Lands and Nations

Every `/lands ...`/`/nations ...` command acts on your own edit land/its nation - normally you'd use
`/lands edit <land>` to switch between your own lands. With `lands.admin.command.edit`, that same
command also accepts a land you aren't a member of, so `/lands edit <land>` followed by the normal
player commands (`/lands claim`, `/lands member trust`, `/nations chat`, ...) is how staff manage
any land or nation on the server. That permission may also ignore requirements such as max members
for some commands, but never suppresses correctness checks (e.g. a player who's already trusted
still can't be re-trusted without an error).

# Open Another Player's Menu

`/lands menu <player>` opens the Lands menu view for a player.

Permission: `lands.admin.command.menu`

# Chat Spy

`/lands admin chatspy <land or nation or *>` toggles chat spy for one land, one nation, or all lands and nations.

Run `/lands admin chatspy` without an argument to disable all selected chat spy targets.

Permission: `lands.admin.command.chatspy`

# Teleport Other Players

Random teleport another player with `/lands rtp <world> <player> [skip-cooldown]`.

Permission: `lands.admin.command.wild`

# Leaderboard Holograms

| Command | Permission |
| --- | --- |
| `/lands admin hologram create <context> <sorting>` | `lands.admin.command.hologram.create` |
| `/lands admin hologram list` | `lands.admin.command.hologram.list` |
| `/lands admin hologram delete` | `lands.admin.command.hologram.delete` |

A supported hologram provider must be installed.

# Permission Debugging

`/lands admin listperms <player>` lists permissions detected for a player.

Permission: `lands.admin.command.listperms`

This is useful when a wildcard or inherited group gives a player access that is hard to spot.
