This page explains how to link containers and control where items go.

# Links
Links are destination containers for a hopper. When the hopper transfers items, it tries to send them to its linked containers.

To create a link:
1. Open the hopper menu.
2. Click `Link to Containers`.
3. Click the destination container.

Left-click starts link mode. Right-click starts unlink mode. Shift-click keeps the mode enabled so you can link or unlink multiple containers. Use `/upgradeablehoppers abort` to leave link or unlink mode.

Linked containers must usually:
* Be in the same world as the hopper.
* Be within the hopper's maximum link distance.
* Be a container type allowed by the server.
* Be inside a claim or region where you are trusted, if the server enforces that.

# Links Menu
Open the `Links` item in the hopper menu to manage linked containers.

In the links menu, you can:
* Open a link's filter.
* Rename a link.
* Unlink a destination.
* Move links up or down when insert-by-order is enabled.

The `Insert by Order` toggle controls whether accepted items should prefer the first matching link. If it is disabled, items can be distributed across available matching links instead.

# Filters
Each link can have its own filter.

To add an item to a filter, open the link filter menu and click the item in your inventory. To remove an item from the filter, click it in the filter list.

## Blacklist and Whitelist
Blacklist mode blocks the items listed in the filter.

Whitelist mode only allows the items listed in the filter.

## Strict Filtering
Strict filtering compares more than the item type. It can also compare item details such as name, lore, enchants, durability, and other item data.

Use strict filtering when you need to separate special items from normal items of the same material.

## Copy Filters
The filter menu can copy one link's filter and paste it into another link. You can also paste a filter to all other links of the same hopper.
