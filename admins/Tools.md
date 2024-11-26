As a server admin or moderator with given staff permissions you can edit everything for players.

# Open Menu of Player
`/lands menu <player>`
This command opens the GUI view of a specific player. This allows you to edit all their settings and lands.\
*Permission: lands.admin.command.menu*

# Edit other Lands
`/lands edit <land>`\
This will enter the edit mode for the land and all following commands will be executed for it.\
*Permission: lands.admin.command.edit*

# Chat Spy
`/lands admin chatspy <land or nation>`\
Spy the chat of a land. You can spy the chat of multiple lands at the same time. To remove a land from the chat spy, just execute the command again with the land parameter. To disable chat spy for all lands, just execute `/lands chatspy`.\
*Permission: lands.admin.command.chatspy*

# Teleport other Players
You can teleport players via the console or as an admin.
_Permission: lands.admin.command.edit_

## Random Teleport
Just execute ``/lands wild <world> <player>`` and replace ``<world>`` with the world and ``<player>`` with the player.

## Teleport to Spawn
Just execute ``/lands spawn <land> <area> <player> <wait>``. 
* You can use ``none`` for the ``<land>`` parameter to teleport to the current edit land of the player.
* Use ``none`` for the ``<area>`` parameter to teleport to the land spawn and not an area spawn. The ``none`` parameter is only available for server admins with the _lands.admin.command.edit_ permission and doesn't tab complete.
* The ``<wait>`` parameter defines, if the player must wait before teleportation.

### Examples
In these examples the ``<player>`` and ``<wait>`` parameters aren't replaced. You need to change them accordingly.

* Teleport to the players edit land spawn: ``/lands spawn none none <player> <wait>``
* Teleport to a specific land spawn: ``/lands spawn <land> none <player> <wait>``
* Teleport to a specific area of a specific land: ``/lands spawn <land> <area> <player> <wait>``