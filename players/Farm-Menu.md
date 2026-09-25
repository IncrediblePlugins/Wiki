# Farm Menu

Open the farm menu by left-clicking the placed farm item if your role can upgrade or manage that farm. You can also use `/farm list` and select one of your own farms.

Right-clicking the placed farm opens storage directly.

# Status

The status item shows whether the farm is running or paused.

Common paused states:

| Status | What to do |
| --- | --- |
| Fuel empty | Add valid fuel items in the fuel menu. |
| Storage full | Collect items from storage or connect an upgradeable hopper if your server supports it. |
| No blocks | Place harvestable blocks inside the farm radius. |
| Owner offline | The farm type requires the owner to be online. The farm continues when the owner returns. |
| Paused manually | Click the status item again to resume, if the other requirements are met. |

Players with configure access can click the status item to pause or resume a manually paused farm.

# Storage

The storage menu contains the harvested items produced by the farm.

Click an item to collect it, or use **Collect All** to move as much as possible into your inventory. If your inventory does not have enough space, the remaining items stay in the farm storage.

Upgrading **Storage Capacity** increases the number of storage slots. When storage is full, the farm pauses until space is available.

## Auto-Sell

If your server has set a sell price on this farm type's harvested items, the storage menu shows an **Auto-Sell** toggle. When enabled, sellable items are sold automatically for currency instead of being stored or moved into a hopper - items without a sell price are unaffected and stay in storage as usual. Auto-sell and hopper output cannot be used at the same time on the same farm.

The toggle only appears if the farm type has at least one sellable item and you have permission to see it.

# Fuel

Some farm types require fuel. Open the fuel menu, place valid fuel items into the fuel slots, and close the menu to add the fuel time.

Use the **Fuel Items** page in the menu to see which items your server accepts and how much time each item adds.

If your server enabled fuel purchases, the fuel menu also has a **Buy Fuel** option that adds fuel time directly for currency, up to the farm's maximum fuel cap.

If your fuel runs low, you get a one-time warning message while you're online, before the farm actually pauses.

# Upgrades

A farm has one combined level, not separate upgrade categories - buying the next level can grow growth interval, radius, and storage capacity together in a single purchase, however the server has configured that level. The menu shows the current and next level's values for each of those before you buy.

Upgrades can cost money, experience, levels, or configured item currency. Some servers require the `betterfarming.upgrade` permission before any farm can be upgraded.

If the next level grows the farm's radius, that specific purchase can fail if the larger farm would overlap another farm or reach into a claim where you are not trusted, and on some servers, if the newly-covered area isn't inside a claim at all. A level that doesn't grow the radius (for example, a storage-only level after radius/interval are already maxed) isn't affected by any of this.

# Stacking

If your server enables it, placing another matching farm item (same type, same level) anywhere inside an existing farm's own protected area merges it into that farm instead of failing as an overlap. The **Stacked** item in the farm menu shows the current amount and the maximum for that farm.

A stacked farm gets more storage capacity and grows faster, both scaling with the stack amount - it still only covers the same area as a single farm at that level, and still only runs out of fuel over about the same real time as an unstacked farm, since it just gets far more done in that time.

Breaking a stacked farm removes one from the stack (or the whole stack at once, if your server enables that) and gives you a farm item back, the same way removing a single farm does.

# Harvestable Blocks

The **Harvestable Blocks** page shows which blocks this farm type can use.

Only configured blocks placed inside the farm radius are tracked. If a farm says it has no blocks, check this page and place one of the listed blocks near the farm.

# Public Access

The **Public** option lets other players use public farm actions: planting, harvesting, and interacting. Opening the farm uses the interact action, so keep a farm private if you do not want other players to use farm interactions such as storage access on a default setup.

Public access does not give players management access, upgrades, or deletion.

# Hopper Output

If your server has UpgradeableHoppers support enabled, place an upgradeable hopper directly underneath the farm. BetterFarming can then move harvested items from farm storage into the hopper for transport.

# Your Farms List

`/farm list` shows every farm you placed, with an overview item and two bulk actions that act on all of them at once:

| Action | What it does |
| --- | --- |
| **Collect All Storage** | Collects storage from every farm you own into your inventory, as much as fits. |
| **Refuel All** | Refuels every farm you own using the fuel item in your hand. |

Both actions tell you what happened: nothing to collect, your inventory is full, only part of it fit, or how much was collected/refueled and from how many farms. Refuel All also tells you if you're not holding an item, or if the item you're holding isn't valid fuel for any farm that needs it.

Refuel All does not simply dump your held item into the first farm it finds. It refuels whichever of your farms currently has the least fuel first, spreading the item across farms so the lowest ones catch up before an already-full farm gets any more - so a large stack of fuel does not get wasted topping off one farm while another sits empty.
