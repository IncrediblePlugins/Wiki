# Usage
Allows players to link their Minecraft and Discord account.

# Setup
1. Optional: Migrate existing links via ``/discordbridge account admin migrate``.
2. If you want to limit who can link their Minecraft accounts, setup allowed roles by executing ``/config linking_allowed_roles add <role>`` in the Discord server.
3. You can setup roles to be given to linked players in Discord, by executing ``/config linking_roles add`` in the Discord server. If you add a role, it will be given to existing linked players as well. This might take a while though, since updates are scheduled to improve the experience for large servers. If you remove a role, you need to manually remove this role from its members, if you wish to.
4. You can setup [LuckPerms](https://www.spigotmc.org/resources/luckperms.28140/) groups to be given to linked players in-game, by executing ``/config linking_groups add`` in the Discord server. If you add a group, it will be given to existing linked players as well. This might take a while though, since updates are scheduled to improve the experience for large servers. If you remove a group, you need to manually remove this group from its members, if you wish to.

# Commands
>`/discordbridge acccount link`\
`Permission: discordbridge.command.account.link`\
Description: Link Discord and Minecraft account.

>`/discordbridge acccount unlink`\
`Permission: discordbridge.command.account.unlink`\
Description: Unlink Discord and Minecraft account.

## Administrator Commands
> `/discordbridge account admin migrate`\
`Permission: discordbridge.admin.command.account.admin.migrate`\
Description: Migrate linked accounts from another plugin.

# PlaceholderAPI Placeholders
Requires [PlaceholderAPI](https://www.spigotmc.org/resources/placeholderapi.6245/) to be installed.

> **`%discordbridge_module_linking_state_bool%`**\
> Description: Returns "true" if the player has their account linked and "false", if their account isn't linked.

> **`%discordbridge_module_linking_state%`**\
> Description: Whether the account is linked. Returns entry from the locale file.
