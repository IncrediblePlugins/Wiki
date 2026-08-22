# Admin Commands

Admin commands are for server staff. Do not give these permissions to regular players.

# Minecraft Admin Commands

Most `/discordbridge admin` subcommands use the permission format `discordbridge.admin.command.<subcommand>`.

| Command | What it does | Permission |
| --- | --- | --- |
| `/discordbridge admin reload` | Reloads configuration and messages. Options marked as requiring restart still need a restart. | `discordbridge.admin.command.reload` |
| `/discordbridge admin about` | Shows plugin information. | `discordbridge.admin.command.about` |
| `/discordbridge admin modules` | Lists enabled DiscordBridge modules. | `discordbridge.admin.command.modules` |

The `/discord` alias may also be available, depending on your server setup.

# Account Migration

| Command | What it does | Permission |
| --- | --- | --- |
| `/discordbridge account admin migrate discordsrv` | Migrates linked accounts from DiscordSRV. | `discordbridge.admin.command.account.admin.migrate` |

Run migrations when the linking module is enabled and the source plugin is installed and up to date.

# Discord Admin Commands

Discord settings are managed with the `/config` slash command in Discord.

| Command | What it does |
| --- | --- |
| `/config set <setting> <value-option>` | Sets a DiscordBridge or ticket setting for the current Discord server. Example: `/config set chat_channel textchannel:#minecraft-chat`. |
| `/config set <setting>` | Removes a setting value, if the setting supports being unset. |
| `/config <collection-setting> add/remove ...` | Adds or removes list entries, such as allowed linking roles or linking role sync rules. |
| `/config type ...` | Manages ticket types. |
| `/config field ...` | Manages ticket form fields. |
| `/config info ...` | Manages predefined information requests for tickets. |
| `/config reason ...` | Manages predefined ticket action reasons. |

See [Discord Configuration](Discord-Configuration.md) for the available keys and ticket setup commands.

# Ticket Staff Commands

These commands are registered by the ticket module and are used inside ticket channels.

| Command | What it does |
| --- | --- |
| `/ticket add member:<member>` | Adds a Discord member to the current ticket, if the command is available to the user. |
| `/ticket assign [member]` | Assigns the ticket to a support member, or to yourself if no member is given. Requires the configured support role. |
