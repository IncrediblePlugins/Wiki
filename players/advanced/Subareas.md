Subareas are smaller areas inside a land.

> This page describes the latest plugin version. If these commands don't work on your server, it
> may still be running an older version where you select a land first with `/lands edit <land>`
> before running commands against it.

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

# Create or Resize a Subarea

1. Use `/lands selection`.
2. Select the two corners of the area.
3. Use `/land <land> area <area> resize`.

If the area does not exist yet, Lands creates it. If it already exists, Lands resizes it to your selection.

Use `/lands selection expand` if you want the area to use the full height. If your selection is very short, Lands may ask you to confirm or expand it.

# Open a Subarea Menu

Stand inside the subarea and use `/lands menu here`.

You can also open the areas list from `/lands` and choose the area there.

# Trust Players in a Subarea

Use `/land <land> area <area> member add <player>` to give the player access only to that area, unless they are also trusted in the whole land.

To remove them from that area, use `/land <land> area <area> member remove <player>`.

# Area Roles and Flags

Each subarea can have its own roles and flags. Open the area menu to decide what players can do there.

This is useful when one player should build in a farm but not open storage, or when a tenant should only control their rented room.

# Rentals

Subareas can be rented or sold if your server has rentals enabled.

See [Rent & Sell System](Rental.md) for details.
