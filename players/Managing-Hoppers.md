This page explains the most important options in the hopper menu.

# Main Menu
Open the hopper menu by left-clicking your hopper without sneaking. Right-click it instead to view its 5 internal item slots directly, like a vanilla hopper.

## Upgrades
A hopper has a single level. Buying an upgrade raises all of these together, in one purchase:
* `Transfer Amount` - how many items the hopper can transfer each cycle.
* `Suction Radius` - how far away dropped items can be picked up.
* `Links Amount` - how many destination containers the hopper can have.
* `Max Link Distance` - how far away linked containers may be.

Upgrade prices and maximum levels depend on the server configuration.

## Stacking
If enabled by the server, several hoppers of the same type and level can share a single block, instead of taking up a separate one each. A stacked hopper transfers and links proportionally more per cycle.

To stack hoppers, click the "stack" item in a hopper's menu while holding a matching hopper item somewhere in your inventory - it doesn't need to be in your hand.

A plain click on a hopper always opens its menu, so breaking one always means sneaking. Depending on server settings, sneak-breaking a stacked hopper either takes the whole stack at once, or just one hopper out of it at a time, leaving the rest in place.

## Suction
The suction option controls the active pickup radius of the hopper. You can increase or decrease the current radius in the hopper menu, up to the level you have unlocked.

If the current radius is set to `0`, the hopper uses vanilla suction behavior instead.

You can also toggle suction visualization from this menu to see the pickup area.

## Redstone
Servers can configure powered hoppers to stop transferring items.

If your hopper stops moving items when powered by redstone, remove the signal or ask a server admin whether redstone pause is enabled.

## Name
Use the name item in the hopper menu to set a custom name. This name is shown in menus such as your hopper list.

## Delete Items
The `Delete Items` toggle controls what happens to items that do not match any linked container filter.

If this is enabled, items that do not fit any filter may be deleted instead of staying in the hopper. Use this carefully.

# Hopper List
Command: `/upgradeablehoppers list`\
Open a list of your placed hoppers.

In the list menu, you can usually:
* Left-click a hopper to open its menu.
* Right-click a hopper to teleport to it.
* Press the drop key on a hopper entry to delete it.

Teleportation can cost money and may have a short wait time, depending on server settings. If the destination is unsafe, the plugin may ask you to confirm with `/upgradeablehoppers confirmtp`.

# Visualization
Command: `/upgradeablehoppers view`\
Toggle particles for nearby hoppers and their links. Run the command again to disable the visualization.
