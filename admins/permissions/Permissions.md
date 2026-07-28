# Permissions

Use a permission plugin such as LuckPerms to assign Lands permissions. Players with operator status usually have every permission, so test with real permission groups when possible.

Limits such as max lands, chunks, members, and upkeep limits are configured in `player-limits.yml`. See the general limits guide for those.

# Command Permissions

| Permission | Gives access to |
| --- | --- |
| `lands.command.*` | All player `/lands` commands (including `/land`, `/claim`). |
| `nations.command.*` | All player `/nations` commands (including `/nation`). |
| `lands.admin.command.*` | All `/lands admin` commands. Staff only. |

There is no standalone `/wars` command or `wars.*` permission tree - war commands live under
`/land <land> war ...` and `/nation <nation> war ...`, covered by `lands.command.*` /
`nations.command.*` above. Force-starting or force-ending a war is covered by
`lands.admin.command.*` (`/lands admin land <land> war start`/`end`).

For the exact admin command list, see [Admin Commands](../Commands.md).

For player command permission nodes, see [Player Commands](Player-Commands.md).

# Flag Permissions

Flags have their own permission nodes.

| Flag type | Permission format | Full list |
| --- | --- | --- |
| Natural flag toggle permissions | `lands.setting.<flag>` | [Natural Flags](../configuration/Natural-Flags.md) |
| Land role flag toggle permissions | `lands.role.setting.<flag>` | [Roles and Role Flags](../configuration/Roles-and-their-Flags.md) |
| Land role flag bypass permissions | `lands.bypass.<flag>` | [Roles and Role Flags](../configuration/Roles-and-their-Flags.md) |
| Protected wilderness role bypass permissions | `lands.bypass.wilderness.<flag>` | [Roles and Role Flags](../configuration/Roles-and-their-Flags.md) |
| Nation role flag toggle permissions | `nations.setting.<flag>` | [Roles and Role Flags](../configuration/Roles-and-their-Flags.md) |
| Nation role flag bypass permissions | `nations.bypass.<flag>` | [Roles and Role Flags](../configuration/Roles-and-their-Flags.md) |
| Personal setting toggle permissions | `lands.player.setting.<flag>` | [Player Personal Settings](../configuration/Player-Personal-Settings.md) |

# Teleport Permissions

These permissions limit teleport actions started by Lands. They are set to `true` by default in `plugin.yml`. If you want to block one of them, set the permission to `false` in your permission plugin.

Example with LuckPerms: `/lp group default permission set lands.teleport.sub_area false`

| Permission | Allows |
| --- | --- |
| `lands.teleport.chunk` | Teleporting to claimed chunks from `/land <land> claim list`. |
| `lands.teleport.rentable` | Teleporting to rentable areas or areas for sale. |
| `lands.teleport.land_spawn` | Teleporting to a land spawn. |
| `lands.teleport.random_teleport` | Random teleporting with `/lands rtp`. |
| `lands.teleport.war` | Teleporting to a war spawn with `/land <land> war spawn` or `/nation <nation> war spawn`. |
| `lands.teleport.sub_area` | Teleporting to a sub area. |
| `lands.teleport.unstuck` | Teleporting with `/lands unstuck`. |

# General Bypass Permissions

| Permission | Allows |
| --- | --- |
| `lands.bypass.*` | All Lands bypass permissions. Staff only. |
| `lands.bypass.selection` | Bypass other plugins cancelling a Lands selection. |
| `lands.bypass.land_claim_border` | Bypass the configured claim distance to other lands. |
| `lands.bypass.shape` | Bypass the configured claim shape restriction. |
| `lands.bypass.encirclement` | Bypass encirclement prevention. |
| `lands.bypass.member.untrust` | Untrust players or remove invites in other players' lands. |
| `lands.bypass.spawn.private` | Teleport to private land spawns. |
| `lands.bypass.expiration` | Bypass land expiration. Requires LuckPerms support. |
| `lands.bypass.priority` | Ignore role priority checks when managing members or roles. |
| `lands.bypass.wilderness.worldedit` | Use WorldEdit in worlds protected by wilderness restrictions. |

# Cooldown Bypass Permissions

| Permission | Allows |
| --- | --- |
| `lands.bypass.cooldown.wild` | Bypass `/lands rtp` cooldown. |
| `lands.bypass.cooldown.rename_land` | Bypass `/land <land> rename` cooldown. |
| `lands.bypass.cooldown.teleport` | Bypass chunk teleport cooldown. |
| `lands.bypass.cooldown.spawn` | Bypass `/land <land> spawn` cooldown. |
| `lands.bypass.cooldown.unstuck` | Bypass `/lands unstuck` cooldown. |
| `nations.bypass.cooldown.rename_nation` | Bypass `/nation <nation> rename` cooldown. |

# War Bypass Permissions

| Permission | Allows |
| --- | --- |
| `lands.bypass.war.trust` | Trust players during war. |
| `lands.bypass.war.claim` | Claim chunks during war. |
| `lands.bypass.war.unclaim` | Unclaim chunks during war. |
| `lands.bypass.cmd.war` | Bypass the command blacklist from `wars.yml`. |

# Command Blacklist Bypass Permissions

| Permission | Allows |
| --- | --- |
| `lands.bypass.cmd.untrusted.*` | Bypass the untrusted-player command blacklist from `config.yml`. |
| `lands.bypass.cmd.untrusted.<command>` | Bypass the untrusted-player blacklist for one command. |
| `lands.bypass.cmd.general.*` | Bypass the general command blacklist from `config.yml`. |
| `lands.bypass.cmd.general.<command>` | Bypass the general blacklist for one command. |

Replace `<command>` with the command name without `/`.

# Teleport Bypass Permissions

| Permission | Allows |
| --- | --- |
| `lands.bypass.teleport.delay` | Skip teleport delay. |
| `lands.bypass.teleport.cmd` | Execute commands while waiting for teleportation. |

# Non-command Admin Permissions

| Permission | Allows |
| --- | --- |
| `lands.admin.*` | All Lands admin actions. Staff only. |
| `lands.admin.disabled-features` | Use some features that are disabled for regular players, such as claiming in disabled worlds or setting rental areas while rent is disabled. |
| `lands.admin.command.edit` | Manage any land through `/land <land>` / `/lands land <land>`, even if not a member. May also ignore requirements such as max members for some commands. |
| `lands.admin.land_delete` | Delete other players' lands or unclaim chunks from them. |
| `lands.admin.land_setowner` | Use `/land <land> member setowner` for lands the player does not own. |
| `lands.admin.setting_edit_land` | Edit natural flags of other players' lands. |
| `lands.admin.setting_edit_role` | Edit role flags of other players' lands. |
| `lands.admin.setting_edit_taxes` | Edit tax settings of other players' lands. |
| `lands.admin.sign.top` | Create and edit leaderboard signs. |
| `nations.admin.nation_edit` | Manage any nation through `/nation <nation>` / `/nations nation <nation>` as if trusted in it, and bypass nation level requirements when creating a nation. |

# Wildcard Groups

Wildcard groups are useful for staff, but use them carefully.

| Permission | Gives |
| --- | --- |
| `lands.*` | All Lands permissions listed under the Lands permission tree (includes war commands/bypasses). |
| `nations.*` | All Nations permissions listed under the Nations permission tree. |
