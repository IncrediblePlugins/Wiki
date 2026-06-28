# Recommended Permission Setup

This is a starting point for a normal survival server. Adjust it to your server's rules and disabled features.

Use a permission plugin such as LuckPerms. If you want to block one permission that is granted by a wildcard, set the specific permission to `false`.

# Regular Players

Recommended broad permissions:

```text
lands.command.*
nations.command.*
wars.command.*
lands.teleport.*
lands.setting.*
lands.role.setting.*
lands.player.setting.*
nations.setting.*
```

These allow players to use the normal player commands, teleport features, and the land/nation settings that are meant to be player-editable.

# Optional Player Permissions

Give these only if the matching feature should be available:

| Permission | Use when |
| --- | --- |
| `nations.command.*` | Nations are enabled. |
| `wars.command.*` | Wars are enabled. |
| `lands.command.rent` | Renting or selling areas is enabled. |
| `lands.command.createcamp` | Camps are enabled. |
| `lands.command.storage` | Land storage is enabled. |

# Staff

Do not give staff wildcards to regular players.

| Permission | Use |
| --- | --- |
| `lands.admin.command.*` | All Lands admin commands. |
| `wars.admin.command.*` | All Wars admin commands. |
| `lands.admin.command.chatspy` | Chat moderation. |
| `lands.bypass.*` | All Lands bypass permissions. Give only to trusted staff. |
| `lands.admin.*` | All non-command admin actions. Give only to trusted staff. |
| `nations.admin.*` | Nation admin actions. |

# More Detail

See [Permissions](Permissions.md) for the full permission reference and [Admin Commands](../Commands.md) for all admin command permissions.
