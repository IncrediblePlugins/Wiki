# Permissions

To assign permissions to players, install a permissions plugin such as [LuckPerms](https://www.spigotmc.org/resources/28140).

Players with `/op` have all Bukkit permissions.

# Player Permissions

These permissions are safe to set for your players.

| Permission | What it allows |
| --- | --- |
| `discordbridge.command.help` | Use `/discordbridge help`. |
| `discordbridge.command.account.link` | Use `/discordbridge account link` and `/account link`. |
| `discordbridge.command.account.unlink` | Use `/discordbridge account unlink` and `/account unlink`. |
| `discordbridge.command.account.*` | Use all account subcommands. |
| `discordbridge.command.invite` | Use `/discordbridge invite`, if the invite command is enabled. |

See [Player Commands](../players/Commands.md) for the player command reference.

# Admin Permissions

These permissions should only be given to server admins.

| Permission | What it allows |
| --- | --- |
| `discordbridge.admin.command` | Access to the `/discordbridge admin` command tree. |
| `discordbridge.admin.command.reload` | Use `/discordbridge admin reload`. |
| `discordbridge.admin.command.about` | Use `/discordbridge admin about`. |
| `discordbridge.admin.command.modules` | Use `/discordbridge admin modules`. |
| `discordbridge.admin.command.account.admin.migrate` | Use `/discordbridge account admin migrate`. |
| `discordbridge.admin.command.*` | Use all DiscordBridge admin commands. |
| `discordbridge.admin.*` | Use all DiscordBridge admin permissions. |
| `discordbridge.*` | Use all DiscordBridge permissions. |

See [Admin Commands](../admins/Commands.md) for command details.

# Discord Permissions and Roles

Discord slash commands use Discord permissions and DiscordBridge's Discord-side configuration.

| Access | How to configure it |
| --- | --- |
| Bot configuration | Give the member Discord administrator permission or set `administrator_role` with `/config set administrator_role role:<role>`. |
| Ticket staff | Set `tickets_role_support` with `/config set tickets_role_support role:<role>`. |
| Account linking limit | Add roles with `/config linking_allowed_roles add role:<role>`, or leave the list empty to allow all Discord members to link. |
| Lands channel management | The linked Minecraft account must own the land or nation, unless the Discord member has administrator permission. |

See [Discord Configuration](../admins/Discord-Configuration.md) for the available Discord settings.
