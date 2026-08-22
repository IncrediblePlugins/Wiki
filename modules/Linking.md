# Usage

Allows players to link their Minecraft and Discord accounts.

# Setup

1. Optional: Migrate existing links via ``/discordbridge account admin migrate discordsrv``.
2. Optional: If you want to limit who can link Minecraft accounts, add allowed roles with ``/config linking_allowed_roles add role:<role>`` in the Discord server.
3. Optional: Give linked players Discord roles with ``/config linking_roles add ingame_permission:<permission> discord_role:<role>``. If you add a role, it will be given to existing linked players as well. This may take a while on large servers. If you remove a role, manually remove it from members if needed.
4. Optional: Give linked players [LuckPerms](https://www.spigotmc.org/resources/luckperms.28140/) groups in-game with ``/config linking_groups add discord_role:<role> ingame_group:<group>``. If you add a group, it will be given to existing linked players as well. This may take a while on large servers. If you remove a group, manually remove it from players if needed.
5. Optional: Edit `DiscordBridge/Modules/linking.yml` for forced linking, name sync, and one-time reward commands.

## Name Sync Exclude Users

You can exclude users from name sync with ``/config linking_name_sync_ignore_roles add role:<role>`` in the Discord server. If a user has any of these roles, their nickname won't be synchronized with the in-game player.

# Minecraft Commands

| Command | What it does | Permission |
| --- | --- | --- |
| `/discordbridge account` | Opens the account linking menu. | none |
| `/account` | Shortcut for `/discordbridge account`. | none |
| `/discordbridge account link` | Creates a Discord verification code. | `discordbridge.command.account.link` |
| `/account link` | Shortcut for creating a Discord verification code. | `discordbridge.command.account.link` |
| `/discordbridge account unlink` | Unlinks the player's Discord account. | `discordbridge.command.account.unlink` |
| `/account unlink` | Shortcut for unlinking. | `discordbridge.command.account.unlink` |

# Discord Commands

| Command | What it does |
| --- | --- |
| `/account link code:<code>` | Links the Discord account to the Minecraft account that generated the code. |
| `/account unlink` | Unlinks the Discord account from Minecraft. |

## Administrator Commands

`/discordbridge account admin migrate discordsrv`\
Migrates linked accounts from DiscordSRV.\
_Permission: discordbridge.admin.command.account.admin.migrate_

# Player Guide

Player-facing linking usage is documented in [Account Linking](../players/Account-Linking.md).

# PlaceholderAPI Placeholders
Requires [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) to be installed.

`%discordbridge_module_linking_amount%`\
The amount of players that have linked their accounts.

`%discordbridge_module_linking_user_state_bool%`\
Returns `true` if the player has their account linked and `false`, if their account isn't linked.

`%discordbridge_module_linking_user_state%`\
Whether the account is linked. Returns entry from the locale file.

`%discordbridge_module_linking_user_id%`\
Returns the ID of the linked Discord user.

`%discordbridge_module_linking_user_name%`\
Returns the name of the linked Discord user.

`%discordbridge_module_linking_user_booster%`\
Returns whether user has boosted any server that the bot is added to.

`%discordbridge_module_linking_user_booster_bool%`\
Returns `true` if the player has boosted any server that the bot is added to and `false`, if they didn't boost any server.
