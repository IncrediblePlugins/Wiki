# Usage
Runs the Discord bot.

# Setup
1. Create an application in your [Discord developer portal](https://discord.com/developers/applications).
    * The bot needs to following scopes: applications.command, bot
    * The bot needs to following bot permissions: Manage Channels, Manage Webhooks, Read Messages/View Channels, Send Messages, Manage Messages, Embed Links, Attach Files, Read Message History, Add Reactions
    * Alternatively you can use the following URL to add the bot with the required permissions. Just make sure to replace ``CLIENT_ID`` with your bots client ID: https://discord.com/api/oauth2/authorize?client_id=CLIENT_ID&permissions=2684480592&scope=bot+applications.commands
2. Copy the bot token and paste it at the ``token`` option in DiscordBridge/Modules/bot.yml.

# Commands
> `/discordbridge invite`\
`Permission: discordbridge.command.invite`\
Description: Get invite to Discord server. Only available if ``invite-url`` is configured in the module config.
