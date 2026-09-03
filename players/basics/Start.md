This page explains the first steps for using Lands.

> This page describes the latest plugin version. If these commands don't work on your server, it
> may still be running an older version where land commands took an explicit `/land <land> ...`
> argument instead of acting on your edit land automatically.

Most commands for an existing land are reached through `/lands ...` (also available as `/land ...`)
and act on your *edit land* - if you're trusted in more than one land, use `/lands edit <land>` to
pick which one.

# 1. Claim Land

Stand where you want to claim and use `/claim` (or `/lands claim`).

If you do not own a land yet, Lands can create one for you named after you and claim the area around you.

If you already have a land and want to add the claim to it instead, use `/lands claim`.

If you want to choose the land name first, use `/lands create [name]` before claiming.

# 2. Claim Larger Areas

Use selection mode when you want to claim more than one chunk at once.

1. Use `/lands selection`.
2. Select two corners.
3. Use `/lands claim`.

Use `/lands selection expand` if you want the selection to use the full height.

# 3. Open the Menu

Use `/lands` or `/lands menu` to open the Lands menu.

The menu lets you manage members, roles, areas, relations, taxes, inbox messages, and other settings that are enabled on your server.

If your server uses money, also read [Economy](../advanced/Economy.md).

If you want to see borders, maps, invites, storage, or safety teleports, read [Map and Tools](Map-and-Tools.md).

# 4. Trust Players

Use `/lands member trust <player>` (or `/trust <player>`) to invite or trust a player in your whole land.

Use `/lands area <area> member trust <player>` to trust them only in a specific area.

You can also trust players from the menu:

1. Open `/lands`.
2. Open the players or members menu.
3. Choose the trust option.

# 5. Remove Players

Use `/lands member untrust <player>` (or `/untrust <player>`) to remove a player from your whole land.

Use `/lands area <area> member untrust <player>` to remove them only from a specific area.

# 6. Manage Permissions

Permissions are controlled by roles. Open `/lands`, go to the roles menu, and edit the role settings.

Use roles to decide what members can do, such as opening containers, building, attacking players, using land spawn, or managing land settings.

# 7. Promote or Demote Members

Open `/lands`, go to the members menu, and click a player.

Depending on your server menu layout, you can promote or demote players from there.
