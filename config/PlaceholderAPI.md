You can display placeholders of DiscordBridge in other plugins with the help of [PlaceholderAPI](https://www.spigotmc.org/resources/6245).
DiscordBridge itself also supports PlaceholderAPI in its locale files etc.

# Placeholders
You can find the placeholders of each module on their own page. Here are only placeholders listed
that don't belong to any module.

## Bot
Link: [Click](https://wiki.incredibleplugins.com/discordbridge/modules/bot#placeholderapi-placeholders)

## Linking
Link: [Click](https://wiki.incredibleplugins.com/discordbridge/modules/linking#placeholderapi-placeholders)

## Other Placeholders
Here are placeholders that don't belong to any module.

### Minecraft Server
DiscordBridge supports Redis and therefore can display information about your whole network. This is useful, if DiscordBridge is installed
on multiple servers, and you want to display combined or information about specific servers.

#### Format
The format is always as follows: `%discordbridge_server_<server>_<placeholder>`\
You need to replace ``<server>`` with the name of the server given in the Redis section of the config or in the ``server-name.txt`` file in the DiscordBridge plugin folder.
You can use ``total`` as the server name to display information for all servers combined, such as the player count on all servers combined.
The ``<placeholder>`` argument needs to be replaced with the specific placeholder.

#### Placeholders
`%discordbridge_server_<server>_players_online%`\
Returns the amount of players online.

Example usage:
* ``%discordbridge_server_total_players_online%`` -> Returns the combined amount of players on all servers
* ``%discordbridge_server_server-1_players_online%`` -> Returns the amount of players on ``server-1``.