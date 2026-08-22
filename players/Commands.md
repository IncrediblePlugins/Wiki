# Player Commands

Some commands only exist if your server enabled the matching module. Your server may also limit commands by permission or Discord role.

# Minecraft Commands

The main command is `/discordbridge`. Many servers also have the `/discord` alias.

The `/account` command is a shortcut for `/discordbridge account`.

| Command | What it does |
| --- | --- |
| `/discordbridge help [page]` | Shows the DiscordBridge commands that you can use. |
| `/discordbridge account` | Opens the account linking menu. |
| `/account` | Opens the account linking menu. |
| `/discordbridge account link` | Creates a Discord verification code for linking. |
| `/account link` | Shortcut for creating a Discord verification code. |
| `/discordbridge account unlink` | Unlinks your Minecraft account from Discord. |
| `/account unlink` | Shortcut for unlinking your Minecraft account from Discord. |
| `/discordbridge invite` | Shows the Discord invite, if the server configured one. |

# Discord Commands

These are slash commands in the Discord server.

| Command | What it does |
| --- | --- |
| `/account link code:<code>` | Links your Discord account to your Minecraft account. Get the code with `/account link` in Minecraft. |
| `/account unlink` | Unlinks your Discord account from Minecraft. |
| `/online` | Shows online Minecraft players. |

# Ticket Commands

Ticket creation usually starts from a ticket panel message, not from a slash command.

| Command | What it does |
| --- | --- |
| `/ticket add member:<member>` | Adds a Discord member to the current ticket, if your server allows it. |

# Lands Discord Commands

These commands only exist if the Lands module is enabled.

| Command | What it does |
| --- | --- |
| `/lands top` | Shows top lands. |
| `/lands channel create land:<land>` | Creates the configured Discord channel for a land. |
| `/lands channel delete name:<land>` | Deletes the Discord channel for a land. The name can be omitted when used inside that land channel. |
| `/lands inbox` | Shows the inbox for the land connected to the current Discord channel. |
| `/nations top` | Shows top nations, if nations are enabled. |
| `/nations channel create nation:<nation>` | Creates the configured Discord channel for a nation. |
| `/nations channel delete name:<nation>` | Deletes the Discord channel for a nation. The name can be omitted when used inside that nation channel. |
| `/nations inbox` | Shows the inbox for the nation connected to the current Discord channel. |

# Minecraft Command Permissions

Server owners decide which players receive these permissions.

| Command | Permission |
| --- | --- |
| `/discordbridge help` | `discordbridge.command.help` |
| `/discordbridge account link` | `discordbridge.command.account.link` |
| `/discordbridge account unlink` | `discordbridge.command.account.unlink` |
| `/discordbridge invite` | `discordbridge.command.invite` |
