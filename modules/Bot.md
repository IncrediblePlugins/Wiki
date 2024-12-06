# Usage
Runs the Discord bot.

# Setup
1. Create an application in your [Discord developer portal](https://discord.com/developers/applications).
    * The bot needs to following scopes: applications.command, bot
    * The bot needs to following bot permissions: Manage Channels, Manage Webhooks, Read Messages/View Channels, Send Messages, Manage Messages, Embed Links, Attach Files, Read Message History, Add Reactions
    * Alternatively you can use the following URL to add the bot with the required permissions. Just make sure to replace ``CLIENT_ID`` with your bots client ID: https://discord.com/api/oauth2/authorize?client_id=CLIENT_ID&permissions=2684480592&scope=bot+applications.commands
2. Copy the bot token and paste it at the ``token`` option in DiscordBridge/Modules/bot.yml.

# Ingame Commands
`/discordbridge invite`\
Get invite to thh Discord server. Only available if ``invite-url`` is configured in the module config.\
_Permission: discordbridge.command.invite_

# PlaceholderAPI Placeholders
Requires [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) to be installed.

## Format
The format is always as follows: `%discordbridge_module_bot_server_<server>_<placeholder>`\
You need to replace ``<server>`` with the ID of the server. You can retrieve the server ID by enabling the developer mode in Discord.
You can use ``total`` as the server ID to display information for all servers combined, such as the user count on all servers combined.
The ``<placeholder>`` argument needs to be replaced with the specific placeholder.

`%discordbridge_module_bot_server_<server>_members_amount%`\
Returns the amount of members.
Example usage:
* ``%discordbridge_module_bot_server_total_members_amount%`` -> Returns the combined amount of members on all servers.
* ``%discordbridge_module_bot_server_server-1_members_amount%`` -> Returns the amount of members on the server with the ID ``1234567891012131415``.
  
`%discordbridge_module_bot_server_<server>_boosters_amount%`\
Returns the amount of guild boosters.

`%discordbridge_module_bot_server_<server>_boosters_contains_<userId>%`\
Returns whether user with the ID ``<userId>`` has boosted the server or any server if ``<server>`` equals ``total``.

`%discordbridge_module_bot_server_<server>_boosters_contains_<userId>_bool%`\
Returns ``true``, if the user with the ID ``<userId>`` has boosted the server or any server if ``<server>`` equals ``total``. Otherwise, returns ``false``.
