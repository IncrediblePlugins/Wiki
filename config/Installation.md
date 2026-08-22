# General

DiscordBridge can be installed on one server or on multiple Minecraft servers.

You can decide which instance hosts the Discord bot by enabling or disabling the Bot module in `DiscordBridge/Modules/bot.yml`.

## Multiple Instances

If you run multiple instances of DiscordBridge, Redis is recommended. Redis lets non-bot instances forward chat and webhook messages to the instance that hosts the Discord bot.

You can also run a separate bot instance on each server if you cannot use Redis. Redis is optional, but recommended for network setups.

# Instance Setup

1. Place the downloaded plugin file in the plugins folder of your server.
2. Start the server.
3. If this instance should host the Discord bot, [set up the bot module](../modules/Bot.md). If it should not run the bot, disable the module in `DiscordBridge/Modules/bot.yml`.
4. Make any changes you need in `config.yml`, especially the `general` and `database` sections.
5. Configure the modules in `DiscordBridge/Modules`.
   * [Chat](../modules/Chat.md)
   * [Linking](../modules/Linking.md)
   * [Lands](../modules/Lands.md)
   * [Events](../modules/Events.md)
   * [Tickets](../modules/Tickets.md)
6. Restart the server. Initial setup and module enable or disable changes require a restart. Some other options require a restart as well; those options say so in their config comments. Otherwise, `/discordbridge admin reload` is sufficient.
7. Optional: Set permissions in your permissions plugin. See [Permissions](../permissions/Permissions.md).
8. Configure Discord-side settings with `/config`. See [Discord Configuration](../admins/Discord-Configuration.md).
