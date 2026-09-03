Subareas are smaller areas inside a land.

> This page describes the latest plugin version. If these commands don't work on your server, it
> may still be running an older version where land commands took an explicit `/land <land> ...`
> argument instead of acting on your edit land automatically.

Unlike normal claims, subareas are based on blocks, not chunks. This means a subarea can cover only part of a chunk and can have its own height range.

Each land also has a default area. The default area is everything in the land that is not inside a subarea.

# What Subareas Are For

Use subareas when different parts of your land need different members or permissions.

For example, you can make:

- a private storage room
- a farm that only some players can use
- a shop area
- a rented room
- a town plot

# Create or Assign a Subarea

1. Use `/lands selection`.
2. Select the two corners of the area.
3. Use `/lands area <area> assign` (or `/assign <area>`).

If the area does not exist yet, Lands creates it. If it already exists, Lands assigns your selection as its new shape. You can also create an empty area first with `/lands area <name> create` and assign a selection to it later.

Use `/lands selection expand` if you want the area to use the full height. If your selection is very short, Lands may ask you to confirm or expand it.

# Open a Subarea Menu

Stand inside the subarea and use `/lands menu here`.

You can also open the areas list from `/lands` and choose the area there.

# Trust Players in a Subarea

Use `/lands area <area> member trust <player>` to give the player access only to that area, unless they are also trusted in the whole land.

To remove them from that area, use `/lands area <area> member untrust <player>`.

# Area Roles and Flags

Each subarea can have its own roles and flags. Open the area menu to decide what players can do there.

This is useful when one player should build in a farm but not open storage, or when a tenant should only control their rented room.

# Rentals

Subareas can be rented or sold if your server has rentals enabled.

See [Rent & Sell System](Rental.md) for details.
