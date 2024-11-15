# General
This plugin can be installed on each of your servers. You can decide which instance should host the Discord bot, by enabling or disabling the Bot module in `DiscordBridge/Modules/bot.yml`.

## Multiple Instances
If you run multiple instances of this plugin, it's recommended to use Redis to forward chat from a in-game server to the instance that hosts the bot. You can also have each instance host their own bot instance, if you can't use Redis. So, Redis is optional, but recommended.

# Instance Setup
1. Place the downloaded plugin file in the plugins folder of your server.
2. Start the server.
3. **If this instance should host the Discord bot:** [Setup the bot module.](https://wiki.incredibleplugins.com/discordbridge/modules/bot) **If you do not wish this instance to run the Discord bot, make sure to disable the module in `/DiscordBridge/Modules/bot.yml.`**
4. Make any changes you wish to `config.yml` (especially the section named `general`), configure the modules located in `/DiscordBridge/Modules`
   * [Chat](https://wiki.incredibleplugins.com/discordbridge/modules/chat)
   * [Linking](https://wiki.incredibleplugins.com/discordbridge/modules/linking)
   * [Lands](https://wiki.incredibleplugins.com/discordbridge/modules/lands)
   * [Events](https://wiki.incredibleplugins.com/discordbridge/modules/events)
   * [Tickets](https://wiki.incredibleplugins.com/discordbridge/modules/tickets)
5. Restart the server. At initial setup and when enabling or disabling modules, a restart is required. Some other options require a restart as well. If so there is a note stating that at the option. Otherwise, executing ``/discordbridge admin reload`` is sufficient.
6. Optional: Set permissions in your permissions plugin: [Link](../permissions/Permissions.md)
